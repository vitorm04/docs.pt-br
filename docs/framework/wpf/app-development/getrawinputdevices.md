---
title: GetRawInputDevices
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
ms.openlocfilehash: 4fc7a5021f9f8d9e6badcd3e13266fb8f4bfe7a4
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991754"
---
# <a name="getrawinputdevices"></a>GetRawInputDevices
Permite ao PresentationHost.exe descobrir e registrar os dispositivos de dados brutos (dispositivos de interface humana) no qual o aplicativo host está interessado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppEnum`  
  
 fora Um ponteiro para um [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) para enumerar os dispositivos de entrada brutos.  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 HRESULT:  
  
 S_OK- [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) será usado somente pelo PresentationHost. exe se S_OK for retornado.  
  
 E_NOTIMPL  
  
## <a name="remarks"></a>Comentários  
 Os dispositivos de entrada brutos são o conjunto de dispositivos de entrada que inclui teclados, mouses e dispositivos menos tradicionais, como controles remotos.  
  
 Depois que a lista de dispositivos de entrada brutos for recuperada, o PresentationHost. exe será registrado com os dispositivos para receber mensagens de notificação WM_INPUT.  
  
## <a name="see-also"></a>Consulte também

- [GetRawInputDeviceList](/windows/desktop/api/winuser/nf-winuser-getrawinputdevicelist)
- [FilterInputMessage](filterinputmessage.md)
