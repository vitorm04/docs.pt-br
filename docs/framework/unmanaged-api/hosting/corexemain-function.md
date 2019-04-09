---
title: Função _CorExeMain
ms.date: 03/30/2017
api_name:
- _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain
helpviewer_keywords:
- _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7407db297a827004c851b904b2da8652778cb08
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177483"
---
# <a name="corexemain-function"></a>Função _CorExeMain
Inicializa o common language runtime (CLR), localiza o ponto de entrada gerenciado no cabeçalho CLR do assembly executável e inicia a execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a>Comentários  
 Essa função é chamada pelo carregador em processos criados a partir de assemblies executáveis gerenciados. Para assemblies DLL, o carregador de chamadas a [cordllmain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function em vez disso.  
  
 Carregador do sistema operacional chama esse método, independentemente do ponto de entrada especificado no arquivo de imagem.  
  
 No Windows 98, Windows ME, Windows NT e Windows 2000, o `_CorExeMain` função é chamada indiretamente por meio de uma correção no carregador do sistema operacional. Todas as outras versões do Windows, ele é chamado diretamente pelo carregador do sistema operacional.  
  
 Para obter mais informações, consulte a seção comentários a [CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) tópico.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Funções estáticas globais de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
