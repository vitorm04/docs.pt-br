---
title: GetRawInputDevices
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
ms.openlocfilehash: acaa3a2ff0f08f60956caedba60c996e01a6eff3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="getrawinputdevices"></a>GetRawInputDevices
Permite ao PresentationHost.exe descobrir e registrar os dispositivos de dados brutos (dispositivos de interface humana) no qual o aplicativo host está interessado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppEnum`  
  
 [out] Um ponteiro para um [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) para enumerar os dispositivos de entrada raw.  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 HRESULT:  
  
 S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) somente será usado por PresentationHost.exe se for retornado S_OK.  
  
 E_NOTIMPL  
  
## <a name="remarks"></a>Comentários  
 Dispositivos de entrada crua são o conjunto de dispositivos de entrada que inclui os teclados e mouses dispositivos menos tradicionais como controles remotos.  
  
 Depois que a lista de dispositivos de entrada crua foi obtida, PresentationHost.exe registra nos dispositivos para receber mensagens de notificação WM_INPUT.  
  
## <a name="see-also"></a>Consulte também  
 [http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp)  
 [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)
