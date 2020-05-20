---
title: Método ISymUnmanagedWriter::OpenMethod
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type:
- apiref
ms.openlocfilehash: d2d16ab0a29fadd3a64d906a64fc46c422e01c45
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610035"
---
# <a name="isymunmanagedwriteropenmethod-method"></a>Método ISymUnmanagedWriter::OpenMethod
Abre um método no qual as informações de símbolo são emitidas. O método fornecido torna-se o método atual para chamadas para definir pontos de sequência, parâmetros e escopos léxicos. Há um escopo lexical implícito em todo o método. Reabrir um método que foi fechado anteriormente apaga todos os símbolos definidos anteriormente para esse método. Pode haver apenas um método Open por vez.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `method`  
 no O token de metadados para o método a ser aberto.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Confira também

- [Interface ISymUnmanagedWriter](isymunmanagedwriter-interface.md)
- [Método CloseMethod](isymunmanagedwriter-closemethod-method.md)
- [Método OpenMethod2](isymunmanagedwriter3-openmethod2-method.md)
