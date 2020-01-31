---
title: Método ICorPublishAppDomain::GetName
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetName
helpviewer_keywords:
- GetName method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetName method [.NET Framework debugging]
ms.assetid: 6ef8ac9b-9803-4b65-8b13-25f3e0b1bc6b
topic_type:
- apiref
ms.openlocfilehash: 4325d61d12a66b17f88e5e368cbbc7806d0a3ec5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790713"
---
# <a name="icorpublishappdomaingetname-method"></a>Método ICorPublishAppDomain::GetName
Obtém o nome do domínio do aplicativo que é representado por este [ICorPublishAppDomain](icorpublishappdomain-interface.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cchName`  
 no O tamanho da matriz de `szName`.  
  
 `pcchName`  
 fora Um ponteiro para o número de caracteres largos, incluindo o caractere nulo, retornado na matriz de `szName`.  
  
 `szName`  
 fora Uma matriz na qual armazenar o nome.  
  
## <a name="remarks"></a>Comentários  
 Se `szName` não for NULL, o método `GetName` copiará até `cchName` caracteres (incluindo o terminador nulo) em `szName`. Se um não nulo for retornado em `pcchName`, o número real de caracteres no nome (incluindo o terminador nulo) será armazenado na matriz de `szName`.  
  
 O método `GetName` retorna um S_OK HRESULT, independentemente de quantos caracteres foram copiados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorPub. idl, CorPub. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorPublishAppDomain](icorpublishappdomain-interface.md)
