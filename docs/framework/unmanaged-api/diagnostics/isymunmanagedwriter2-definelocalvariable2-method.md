---
title: Método ISymUnmanagedWriter2::DefineLocalVariable2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineLocalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type:
- apiref
ms.openlocfilehash: ac7559bd5431f45b266602404ddde9081aa2944d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614689"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a>Método ISymUnmanagedWriter2::DefineLocalVariable2
Define uma única variável no escopo léxico atual. Esse método pode ser chamado várias vezes para uma variável do mesmo nome que tem várias casas em um escopo. Nesse caso, no entanto, os valores dos `startOffset` `endOffset` parâmetros e não devem se sobrepor.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DefineLocalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `name`  
 no O nome da variável local.  
  
 `attributes`  
 no Os atributos da variável local.  
  
 `sigToken`  
 no O token de metadados da assinatura.  
  
 `addrKind`  
 no O tipo de endereço.  
  
 `addr1`  
 no O primeiro endereço para a especificação de parâmetro.  
  
 `addr2`  
 no O segundo endereço para a especificação de parâmetro.  
  
 `addr3`  
 no O terceiro endereço para a especificação de parâmetro.  
  
 `startOffset`  
 no O deslocamento de início da variável. Esse parâmetro é opcional. Se for 0, esse parâmetro será ignorado e a variável será definida em todo o escopo. Se for um valor diferente de zero, a variável se enquadrará dentro dos deslocamentos do escopo atual.  
  
 `endOffset`  
 no O deslocamento de fim da variável. Esse parâmetro é opcional. Se for 0, esse parâmetro será ignorado e a variável será definida em todo o escopo. Se for um valor diferente de zero, a variável se enquadrará dentro dos deslocamentos do escopo atual.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl  
  
## <a name="see-also"></a>Confira também

- [Interface ISymUnmanagedWriter2](isymunmanagedwriter2-interface.md)
- [Método DefineLocalVariable](isymunmanagedwriter-definelocalvariable-method.md)
