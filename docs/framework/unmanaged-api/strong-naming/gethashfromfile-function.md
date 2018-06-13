---
title: Função GetHashFromFile
ms.date: 03/30/2017
api_name:
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f98f888280090bfa613acf6ae37bc60ab63c371e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456508"
---
# <a name="gethashfromfile-function"></a>Função GetHashFromFile
Gera um hash com base no conteúdo do arquivo especificado.  
  
 Essa função foi preterida. Use o [Gethashfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) método em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `szFilePath`  
 [in] O nome do arquivo para hash.  
  
 `piHashAlg`  
 [out no] O algoritmo para usar ao gerar o hash. Os algoritmos válidos são aquelas definidas por CryptoAPI Win32. Se `piHashAlg` for definido como 0, o algoritmo padrão CALG_SHA-1 é usado.  
  
 `pbHash`  
 [out] Uma matriz de bytes que contém o hash gerado.  
  
 `cchHash`  
 [in] O tamanho máximo do buffer que `pbHash` aponta para.  
  
 `pchHash`  
 [out] O tamanho, em bytes, do retornado `pbHash`.  
  
## <a name="remarks"></a>Comentários  
 Essa função é o mesmo que [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), exceto que a especificação de nome de arquivo é ANSI em vez de Unicode.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [Método GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
