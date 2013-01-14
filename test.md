```vb
Private tdc As New TDConnection
Public Sub test()
    Dim connResult As Boolean
    connResult = makeConnection("192.168.1.5", "DEFAULT", "Demo", "alex_alm", "", "8080")
    
    'AddAndEditTest "Cruises", "Test"
    AddTestToCoverage 161, 93
    
End Sub

Private Sub AddTestToCoverage(reqID As Integer, testID As Integer)

' Add tests to requirement coverage.

    Dim coverable As ICoverableReq
    Dim reqF As ReqFactory
    Dim aReq As Req

    Set reqF = tdc.ReqFactory
    Set aReq = reqF.Item(reqID)
    Set coverable = aReq
    coverable.AddTestToCoverage testID

    Set coverable = Nothing
    Set reqF = Nothing
    Set aReq = Nothing
End Sub

Public Sub AddAndEditTest(FolderName$, TestName$)

' Create new test.
' This example assumes that the subject folder containing the
' new test is directly under the root "Subject" folder.

    Dim objTest As test
    Dim folder As SubjectNode
    Dim testF As testFactory
    Dim TreeMgr As treeManager
    Dim Path As String

    Dim Trees As List
    Dim RootName As String
    Dim SubjRoot As SubjectNode

    'tdc is the global TDConnection object.
    Set TreeMgr = tdc.treeManager

    ' Use TreeManager.TreeRoot to get the list of subject
    ' root nodes from the tree manager.
    ' There is only one item in this list.
    Set Trees = TreeMgr.RootList(TDOLE_SUBJECT)

    ' Get the name of the subject tree root in your project.
    RootName = Trees.Item(1)

    Path = RootName & "\" & FolderName

    On Error Resume Next
    Set folder = TreeMgr.NodeByPath(Path)
    On Error GoTo 0

    If folder Is Nothing Then 'Create the folder
        ' Get the SubjectNode root node object from the
        ' tree manager by name.
        Set SubjRoot = TreeMgr.TreeRoot(RootName)
        Set folder = SubjRoot.AddNode(FolderName)
    End If

    Set testF = folder.testFactory
    Dim testFilter As TDFilter
    Set testFilter = testF.Filter
    testFilter.Filter("TS_NAME") = TestName
    Dim testList As List
    Set testList = testF.NewList(testFilter.Text)
    'If testList.Count > 0 Then
        'testF.RemoveItem (TestName.ID)
    'End If
    
    Set objTest = testF.AddItem(Null)
    objTest.Name = TestName
    objTest.Type = "SYSTEM-TEST"
    objTest.Field("TS_USER_04") = "Basic"
    objTest.Field("TS_USER_01") = "Changed"
    objTest.Field("TS_USER_03") = "2-Medium"
    objTest.Post

    
End Sub

Public Function makeConnection(ByVal qcHostName$, qcDomain$, qcProject$, qcUser$, qcPassword$, Optional qcPort) As Boolean

    Dim qcServer As String
    Const fName = "makeConnection" 'For error message

    On Error GoTo makeConnectionErr
    errmsg = ""

    qcServer = "http://" & qcHostName

    If Not (IsMissing(qcPort)) Then
        If Len(qcPort) > 0 Then qcServer = qcServer & ":" & qcPort
    End If

    qcServer = qcServer & "/qcbin"

    
    errmsg = "Failed to create TDConnection"
    If (tdc Is Nothing) Then Set tdc = New TDConnection
    If (tdc Is Nothing) Then GoTo makeConnectionErr
    errmsg = ""

    tdc.InitConnectionEx qcServer
    tdc.Login qcUser, qcPassword

    tdc.Connect qcDomain, qcProject

    makeConnection = True
    
    Exit Function

makeConnectionErr:
    makeConnection = False
    'ErrHandler Err, fName, Err.Description & vbCrLf & errmsg

End Function
 

```
