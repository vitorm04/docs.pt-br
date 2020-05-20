---
title: Interface ISymUnmanagedReader2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2
helpviewer_keywords:
- ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type:
- apiref
ms.openlocfilehash: d4c5ff46d37b1292059b18920abd8042c18bbf31
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615391"
---
# <a name="isymunmanagedreader2-interface"></a>Interface ISymUnmanagedReader2
Representa um leitor de símbolo que fornece acesso a documentos, métodos e variáveis em um repositório de símbolos. Essa interface estende a interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) .  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetMethodByVersionPreRemap](isymunmanagedreader2-getmethodbyversionpreremap-method.md)|Obtenha um método de leitor de símbolo, dado um token de método e um número de versão de edição e continuação.|  
|[Método GetMethodsInDocument](isymunmanagedreader2-getmethodsindocument-method.md)|Obtém todos os métodos que têm informações de linha no documento fornecido.|  
|[Método GetSymAttributePreRemap](isymunmanagedreader2-getsymattributepreremap-method.md)|Obtém um atributo personalizado com base no seu nome.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Confira também

- [Interfaces de armazenamento de símbolo de diagnóstico](diagnostics-symbol-store-interfaces.md)
- [Interface ISymUnmanagedReader](isymunmanagedreader-interface.md)
