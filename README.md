# google
WEnd Sleep(100) $sElement = _WD_FindElement($sSession,$_WD_LOCATOR_ByXPath,"//input[@name='password']") _WD_ElementAction($sSession, $sElement, 'value','nguyenlovetu') $sElement = _WD_FindElement($sSession,$_WD_LOCATOR_ByXPath,"//span[@class='RveJvd snByac']") _WD_ElementAction($sSession, $sElement, 'click')  _WD_WaitElement($sSession,$_WD_LOCATOR_ByXPath,"//span[@class='gb_ab gbsii']")  $Object = _WD_Cookies($sSession,'GetAll')  MsgBox(0,'',$Object)  $Text_Cookie = Json_Decode($Object)  $Name_Cookie = Json_Get($Text_Cookie,'["value"]')  $Value_Cookie = Json_Get($Text_Cookie,'["value"]')  Dim $Cookie[10]  For $o = 0 To UBound($Name_Cookie) - 1     $Cookie[$o] = '{"cookie": {"name": "' &amp; Json_Get($Name_Cookie[$o],'["name"]') &amp; '", "value": "' &amp; Json_Get($Value_Cookie[$o], '["value"]') &amp; '"}}'  Next  _ArrayDisplay($Cookie)  MsgBox(0,'',UBound($Name_Cookie))  _WD_DeleteSession($sSession)  $sSession = _WD_CreateSession($sDesiredCapabilities)  For $o In $Cookie    _WD_Cookies($sSession,'add',$o)  Next  _WD_Navigate($sSession, 'http://www.google.com')
