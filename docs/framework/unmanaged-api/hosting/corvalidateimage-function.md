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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a84869281ec27aface96d722603186382c6e15e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730770"
---
# <a name="corvalidateimage-function"></a>Função _CorValidateImage
Valida imagens de módulo gerenciado e notifica o carregador do sistema operacional, depois de eles terem sido carregados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI _CorValidateImage (   
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ImageBase`  
 [in] Um ponteiro para o local inicial da imagem para validar que o código gerenciado. A imagem já deve ser carregada na memória.  
  
 `FileName`  
 [in] O nome do arquivo da imagem.  
  
## <a name="return-value"></a>Valor de retorno  
 Essa função retorna os valores padrão `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, e `E_FAIL`, bem como os valores a seguir.  
  
|Valor retornado|Descrição|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|A imagem é inválida. Esse valor tem o 0xC000007BL HRESULT.|  
|`STATUS_SUCCESS`|A imagem é válida. Esse valor tem o 0x00000000L HRESULT.|  
  
## <a name="remarks"></a>Comentários  
 No Windows XP e versões posteriores, o carregador do sistema operacional verifica módulos gerenciados examinando o diretório de descritor COM bit no cabeçalho formato COFF. Um bit definido indica que um módulo gerenciado. Se o carregador detecta um módulo gerenciado, ele carrega mscoree. dll e chamadas `_CorValidateImage`, que executa as seguintes ações:  
  
-   Confirma que a imagem é um módulo gerenciado válido.  
  
-   Altera o ponto de entrada na imagem para um ponto de entrada no common language runtime (CLR).  
  
-   Para versões de 64 bits do Windows, modifica a imagem que está na memória transformando-a do formato PE32 para o formato PE32 +.  
  
-   Retorna o carregador quando as imagens de módulo gerenciado são carregadas.  
  
 Para imagens executáveis, o carregador do sistema operacional, em seguida, chama o [CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) função, independentemente do ponto de entrada especificado no executável. Para imagens do assembly DLL, o carregador de chamadas a [cordllmain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) função.  
  
 `_CorExeMain` ou `_CorDllMain` executa as seguintes ações:  
  
-   Inicializa o CLR.  
  
-   Localiza o ponto de entrada gerenciado de cabeçalho CLR do assembly.  
  
-   Inicia a execução.  
  
 As chamadas de carregador a [CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) funcionar quando gerenciado imagens de módulo serão descarregadas. No entanto, essa função não executa nenhuma ação; ele simplesmente retorna.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Funções estáticas globais de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
