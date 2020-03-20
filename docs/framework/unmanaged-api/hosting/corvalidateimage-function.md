---
title: Função _CorValidateImage
ms.date: 03/30/2017
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
ms.openlocfilehash: 3a6da0e845fa50d090cdf0808b211a5806c40961
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178211"
---
# <a name="_corvalidateimage-function"></a>Função _CorValidateImage
Valida imagens gerenciadas do módulo e notifica o carregador do sistema operacional depois de carregado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `ImageBase`  
 [em] Um ponteiro para o local de partida da imagem para validar como código gerenciado. A imagem já deve ser carregada na memória.  
  
 `FileName`  
 [em] O nome do arquivo da imagem.  
  
## <a name="return-value"></a>Valor retornado  
 Esta função retorna `E_INVALIDARG`os `E_OUTOFMEMORY` `E_UNEXPECTED`valores `E_FAIL`padrão, e , bem como os seguintes valores.  
  
|Valor retornado|Descrição|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|A imagem é inválida. Este valor tem o HRESULT 0xC0000007BL.|  
|`STATUS_SUCCESS`|A imagem é válida. Este valor tem o HRESULT 0x0000000L.|  
  
## <a name="remarks"></a>Comentários  
 Nas versões Windows XP e posteriores, o carregador do sistema operacional verifica os módulos gerenciados examinando o bit Com Dscriptor Directory no cabeçalho coff (formato de arquivo de objeto comum). Um bit definido indica um módulo gerenciado. Se o carregador detectar um módulo gerenciado, ele carregará MsCorEE.dll e chamadas, `_CorValidateImage`o que executa as seguintes ações:  
  
- Confirma que a imagem é um módulo gerenciado válido.  
  
- Altera o ponto de entrada na imagem para um ponto de entrada no tempo de execução do idioma comum (CLR).  
  
- Para versões de 64 bits do Windows, modifica a imagem que está na memória, transformando-a do formato PE32 para PE32+.  
  
- Retorna ao carregador quando as imagens do módulo gerenciado forem carregadas.  
  
 Para imagens executáveis, o carregador do sistema operacional então chama a função [_CorExeMain,](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) independentemente do ponto de entrada especificado no executável. Para imagens de montagem DLL, o carregador chama a função [_CorDllMain.](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
  
 `_CorExeMain`ou `_CorDllMain` executa as seguintes ações:  
  
- Inicializa a CLR.  
  
- Localiza o ponto de entrada gerenciado a partir do cabeçalho CLR da montagem.  
  
- Começa a execução.  
  
 O carregador chama a função [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) quando as imagens do módulo gerenciadas são descarregadas. No entanto, essa função não realiza nenhuma ação; ele só retorna.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Funções estáticas globais de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
