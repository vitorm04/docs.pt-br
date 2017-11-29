---
title: "Função GetHashFromFileW"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromFileW
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromFileW
helpviewer_keywords: GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2c19047f03279b1284ea8b5b8f99785cfaff5146
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="gethashfromfilew-function"></a>Função GetHashFromFileW
Gera um hash com base no conteúdo do arquivo especificado por uma cadeia de caracteres Unicode.  
  
 Essa função foi preterida. Use o [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) método em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
#### <a name="parameters"></a>Parâmetros  
 `wszFilePath`  
 [in] O nome de Unicode do arquivo para hash.  
  
 `piHashAlg`  
 [out no] O algoritmo para usar ao gerar o hash. Os algoritmos válidos são aquelas definidas por CryptoAPI Win32. Se `piHashAlg` for definido como 0, o algoritmo padrão CALG_SHA-1 é usado.  
  
 `pbHash`  
 [out] Uma matriz de bytes que contém o hash gerado.  
  
 `cchHash`  
 [in] O tamanho máximo do buffer apontado pelo `pbHash`.  
  
 `pchHash`  
 [out] O tamanho, em bytes, de `pbHash`.  
  
## <a name="remarks"></a>Comentários  
 Essa função é o mesmo que [GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md), exceto que a especificação de nome de arquivo for Unicode em vez de ANSI.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [Método GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
