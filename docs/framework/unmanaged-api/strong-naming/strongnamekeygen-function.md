---
title: Função StrongNameKeyGen
ms.date: 03/30/2017
api_name:
- StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen function [.NET Framework strong naming]
ms.assetid: 883e413a-ad2f-4f7f-b1b9-aeb8fe5b65f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f062f47790136e8cd39c6751b7c75eef660c2b9a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799144"
---
# <a name="strongnamekeygen-function"></a>Função StrongNameKeyGen
Cria um novo par de chaves públicas/privadas para uso de nome forte.  
  
 Esta função foi preterida. Em vez disso, use o método [ICLRStrongName:: StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `wszKeyContainer`  
 no O nome do contêiner de chave solicitado. `wszKeyContainer`deve ser uma cadeia de caracteres não vazia ou NULL para gerar um nome temporário.  
  
 `dwFlags`  
 no Especifica se a chave deve ser desregistrada. Há suporte para os seguintes valores:  
  
- 0x00000000-usado quando `wszKeyContainer` é nulo para gerar um nome de contêiner de chave temporário.  
  
- 0x00000001 (`SN_LEAVE_KEY`) – especifica que a chave deve ser registrada.  
  
 `ppbKeyBlob`  
 fora O par de chaves pública/privada retornado.  
  
 `pcbKeyBlob`  
 fora O tamanho, em bytes, de `ppbKeyBlob`.  
  
## <a name="return-value"></a>Valor de retorno  
 `true`após a conclusão bem-sucedida; caso contrário `false`,.  
  
## <a name="remarks"></a>Comentários  
 A `StrongNameKeyGen` função cria uma chave de 1024 bits. Depois que a chave for recuperada, você deverá chamar a função [StrongNameFreeBuffer](strongnamefreebuffer-function.md) para liberar a memória alocada.  
  
 Se a `StrongNameKeyGen` função não for concluída com êxito, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Método StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [Método StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [Interface ICLRStrongName](../hosting/iclrstrongname-interface.md)
