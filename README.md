# Func-Split_sKey-BRRAVE
Func Split_sKey($sKey)     Local $asArray[3]     If StringInStr($sKey, "\\\") = 1 Then         Local $asComputer = StringRegExp($sKey, "\\\\\\[^\\]*\\", 1)         If Not @error Then             $asArray[0] = StringTrimRight( StringTrimLeft($asComputer[0], 3), 1 )             $sKey = StringReplace($sKey, $asComputer[0], "\", 1)             If Not StringInStr($sKey, "\\") = 1 Then $sKey = StringTrimLeft($sKey, 1)         EndIf     EndIf     If $asArray[0] = "" Then $asArray[0] = @ComputerName     If StringInStr($sKey, "\\") = 1 And Not StringInStr($sKey, "\\\") = 1 Then         Local $asUser = StringRegExp($sKey, "\\\\[^\\]*\\", 1)         If Not @error Then             $asArray[1] = StringTrimRight( StringTrimLeft($asUser[0], 2), 1 )             $sKey = StringReplace($sKey, $asUser[0], "", 1)         EndIf     EndIf     If Not ( StringInStr($sKey, "\") = 1 Or StringInStr($sKey, "\", 0, -1) = StringLen($sKey) Or StringInStr($sKey, "\\") ) Then         $asArray[2] = $sKey     EndIf     Return $asArray EndFunc ;==> Split_sKey  ; #INTERNAL_USE_ONLY# 
