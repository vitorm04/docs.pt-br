---
title: Função StrongNameSignatureGeneration
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGeneration
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration function [.NET Framework strong naming]
ms.assetid: 839b765c-3e41-44ce-bf1b-dc10453db18e
ms.openlocfilehash: d7f481e5c61ec65d2e7414bd47227866f3435028
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176897"
---
# <a name="strongnamesignaturegeneration-function"></a>Função StrongNameSignatureGeneration
Gera uma assinatura de nome forte para o assembly especificado.  
  
 Esta função foi preterida. Use o método [ICLRStrongName::StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
BOOLEAN StrongNameSignatureGeneration (
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `wszFilePath`  
 [em] O caminho para o arquivo que contém o manifesto da montagem para o qual a assinatura de nome forte será gerada.  
  
 `wszKeyContainer`  
 [em] O nome do recipiente de chave que contém o par de chaves público/privado.  
  
 Se `pbKeyBlob` for `wszKeyContainer` nulo, deve especificar um contêiner válido dentro do provedor de serviços criptográficos (CSP). Neste caso, o par de chaves armazenado no recipiente é usado para assinar o arquivo.  
  
 Se `pbKeyBlob` não for nulo, presume-se que o par de chaves esteja contido no objeto grande binário chave (BLOB).  
  
 As teclas devem ser teclas de assinatura Rivest-Shamir-Adleman (RSA) de 1024 bits. Nenhum outro tipo de chaves é suportado neste momento.  
  
 `pbKeyBlob`  
 [em] Um ponteiro para o par de tecla público/privado. Este par está no formato criado pela `CryptExportKey` função Win32. Se `pbKeyBlob` for nulo, o `wszKeyContainer` recipiente de chave especificado por é assumido para conter o par de chaves.  
  
 `cbKeyBlob`  
 [em] O tamanho, em bytes, de `pbKeyBlob`.  
  
 `ppbSignatureBlob`  
 [fora] Um ponteiro para o local para o qual o tempo de execução do idioma comum retorna a assinatura. Se `ppbSignatureBlob` for nulo, o tempo de execução `wszFilePath`armazena a assinatura no arquivo especificado por .  
  
 Se `ppbSignatureBlob` não for nulo, o tempo de execução do idioma comum aloca espaço para retornar a assinatura. O chamador deve liberar este espaço usando a função [StrongNameFreeBuffer.](strongnamefreebuffer-function.md)  
  
 `pcbSignatureBlob`  
 [fora] O tamanho, em bytes, da assinatura retornada.  
  
## <a name="return-value"></a>Valor retornado  
 `true`em conclusão bem sucedida; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 Especifique nulo `wszFilePath` para calcular o tamanho da assinatura sem criar a assinatura.  
  
 A assinatura pode ser armazenada diretamente no arquivo ou devolvida ao chamador.  
  
 Se `StrongNameSignatureGeneration` a função não for concluída com sucesso, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Método StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [Método StrongNameSignatureGenerationEx](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [Interface ICLRStrongName](../hosting/iclrstrongname-interface.md)
