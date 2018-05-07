---
title: Função StrongNameSignatureGenerationEx
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGenerationEx
helpviewer_keywords:
- StrongNameSignatureGenerationEx function [.NET Framework strong naming]
ms.assetid: 9a75469e-aa49-4e32-ad48-3bafd5202f09
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ac2dd50b26137ee4cf06f0545f1f8cf1bfabf80
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="strongnamesignaturegenerationex-function"></a>Função StrongNameSignatureGenerationEx
Gera uma assinatura de nome forte para o assembly especificado, de acordo com os sinalizadores especificados.  
  
 Essa função foi preterida. Use o [: Strongnamesignaturegenerationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) método em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
BOOLEAN StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `wszFilePath`  
 [in] O caminho para o arquivo que contém o manifesto do assembly para o qual a assinatura de nome forte será gerada.  
  
 `wszKeyContainer`  
 [in] O nome do recipiente de chave que contém o par de chaves pública/privada.  
  
 Se `pbKeyBlob` for nulo, `wszKeyContainer` deve especificar um contêiner válido no provedor de serviços de criptografia (CSP). Nesse caso, o par de chaves armazenado no contêiner é usado para assinar o arquivo.  
  
 Se `pbKeyBlob` não for null, o par de chaves é assumido para conter o objeto binário grande (BLOB) chave.  
  
 `pbKeyBlob`  
 [in] Um ponteiro para o par de chaves pública/privada. Esse par está no formato criado pelo Win32 `CryptExportKey` função. Se `pbKeyBlob` é null, o contêiner de chave especificado por `wszKeyContainer` devem para conter o par de chaves.  
  
 `cbKeyBlob`  
 [in] O tamanho, em bytes, de `pbKeyBlob`.  
  
 `ppbSignatureBlob`  
 [out] Um ponteiro para o local para o qual o common language runtime retorna a assinatura. Se `ppbSignatureBlob` é null, o tempo de execução armazena a assinatura no arquivo especificado por `wszFilePath`.  
  
 Se `ppbSignatureBlob` é não nulo, o common language runtime aloca espaço no qual retornar a assinatura. O chamador deve liberar esse espaço usando o [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) função.  
  
 `pcbSignatureBlob`  
 [out] O tamanho, em bytes, da assinatura retornada.  
  
 `dwFlags`  
 [in] Um ou mais dos seguintes valores:  
  
-   `SN_SIGN_ALL_FILES` (0x00000001) - recompilar todos os hashes de módulos vinculados.  
  
-   `SN_TEST_SIGN` (0x00000002) - teste-assinar o assembly.  
  
## <a name="return-value"></a>Valor de retorno  
 `true` Após a conclusão bem-sucedida; Caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 Especifique null para `wszFilePath` para calcular o tamanho da assinatura sem criar a assinatura.  
  
 A assinatura pode ser armazenada diretamente no arquivo ou retornada ao chamador.  
  
 Se `SN_SIGN_ALL_FILES` for especificado, mas não há uma chave pública (ambos `pbKeyBlob` e `wszFilePath` são nulos), hashes de módulos vinculados são recalculados, mas o assembly não está assinado novamente.  
  
 Se `SN_TEST_SIGN` for especificado, o cabeçalho de tempo de execução de linguagem comum não é modificado para indicar que o assembly é assinado com um nome forte.  
  
 Se o `StrongNameSignatureGenerationEx` função não concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método StrongNameSignatureGenerationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)  
 [Método StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
 [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
