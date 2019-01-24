---
title: Método ICLRStrongName::GetHashFromFileW
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromFileW method [.NET Framework hosting]
ms.assetid: c6ff45fc-905d-4c6e-b00c-97c6c7c55d99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2ca00b660a9cbb408fd1175e94a4242dae5f1a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523955"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a>Método ICLRStrongName::GetHashFromFileW
Gera um hash sobre o conteúdo do arquivo especificado por uma cadeia de caracteres Unicode.  
  
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
 [in] O nome do Unicode do arquivo para hash.  
  
 `piHashAlg`  
 [no, out] O algoritmo a ser usado ao gerar o hash. Algoritmos válidos são aquelas definidas por CryptoAPI Win32. Se `piHashAlg` é definido como 0, o algoritmo padrão CALG_SHA-1 é usado.  
  
 `pbHash`  
 [out] Uma matriz de bytes que contém o hash gerado.  
  
 `cchHash`  
 [in] O tamanho máximo do buffer apontado por `pbHash`.  
  
 `pchHash`  
 [out] O tamanho, em bytes, do `pbHash`.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).  
  
## <a name="remarks"></a>Comentários  
 Esse método é igual a [iclrstrongname:: Gethashfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) , exceto que o nome do arquivo especificação é Unicode em vez de ANSI.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Método GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
