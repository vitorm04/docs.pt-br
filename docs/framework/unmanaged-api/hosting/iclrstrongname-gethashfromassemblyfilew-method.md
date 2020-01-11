---
title: Método ICLRStrongName::GetHashFromAssemblyFileW
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW method [.NET Framework hosting]
- GetHashFromAssemblyFileW method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5d0b44a2-5a14-44a2-9a0e-e8682fd4e106
topic_type:
- apiref
ms.openlocfilehash: d98181e0d43206bfbf96182d7e4acf33da486348
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901181"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a>Método ICLRStrongName::GetHashFromAssemblyFileW
Gera um hash sobre o conteúdo do arquivo especificado por uma cadeia de caracteres Unicode.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `wszFilePath`  
 no O caminho para o arquivo a ser transformado em hash. Esse parâmetro deve ser uma cadeia de caracteres Unicode.  
  
 `piHashAlg`  
 [entrada, saída] Uma constante que especifica o algoritmo de hash. Use zero para o algoritmo de hash padrão.  
  
 `pbHash`  
 fora O buffer de hash retornado.  
  
 `cchHash`  
 no O tamanho máximo solicitado de `pbHash`.  
  
 `pchHash`  
 fora O tamanho retornado, em bytes, de `pbHash`.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Método GetHashFromAssemblyFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
