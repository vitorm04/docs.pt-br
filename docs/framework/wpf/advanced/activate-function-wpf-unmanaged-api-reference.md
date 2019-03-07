---
title: Ativar a função (referência de API não gerenciada WPF)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Activate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: ee231653815bd5ef75d58979034e3b3be9f5ba54
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480774"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a>Ativar a função (referência de API não gerenciada WPF)

Essa API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usado diretamente do seu código.

Usado pela infraestrutura do Windows Presentation Foundation (WPF) para gerenciamento do windows.

## <a name="syntax"></a>Sintaxe

```cpp
void Activate(
    const ActivateParameters* pParameters,
    __deref_out_ecount(1) LPUNKNOWN* ppInner,
    );
```

## <a name="parameters"></a>Parâmetros

`pParameters`\
Um ponteiro para os parâmetros de ativação da janela.

`ppInner`\
Um ponteiro para o endereço de um buffer de elemento único que contém um ponteiro para um <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> objeto.

## <a name="requirements"></a>Requisitos

**Plataformas:** Ver [requisitos de sistema do .NET Framework](../../get-started/system-requirements.md).

**DLL:**

No .NET Framework 3.0 e 3.5: PresentationHostDLL.dll

No .NET Framework 4 e posterior: PresentationHost_v0400.dll

**Versão do .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de API não gerenciada do WPF](wpf-unmanaged-api-reference.md)
