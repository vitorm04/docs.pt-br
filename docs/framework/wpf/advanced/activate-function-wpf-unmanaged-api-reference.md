---
title: Ativar a função (referência de API não gerenciada WPF)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Acrivate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: 4931f64a525f14ad5b0b69c582a81cd15d98e541
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a>Ativar a função (referência de API não gerenciada WPF)
Essa API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usado diretamente no seu código.  
  
 Usado pela infraestrutura do Windows Presentation Foundation (WPF) para o gerenciamento do windows.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void Activate(  
    const ActivateParameters* pParameters,  
    __deref_out_ecount(1) LPUNKNOWN* ppInner,  
    );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pParameters  
 Um ponteiro para os parâmetros de ativação da janela.  
  
 ppInner  
 Um ponteiro para o endereço de um buffer único elemento que contém um ponteiro para um <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema do .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **DLL:**  
  
 No .NET Framework 3.0 e 3.5: PresentationHostDLL.dll  
  
 No .NET Framework 4 e posterior: PresentationHost_v0400.dll  
  
 **Versão do .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de API não gerenciada do WPF](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
