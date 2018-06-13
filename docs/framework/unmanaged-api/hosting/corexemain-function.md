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
ms.openlocfilehash: 63af5979b113f81c01c9c68d6cccdfa10811265a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429128"
---
# <a name="corexemain-function"></a>Função _CorExeMain
Inicializa o common language runtime (CLR), localiza o ponto de entrada gerenciado no cabeçalho do executável do assembly CLR e começa a ser executada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a>Comentários  
 Essa função é chamada pelo carregador em processos criado a partir de assemblies gerenciados de executável. Para os assemblies DLL, chama o carregador de [cordllmain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function em vez disso.  
  
 O carregador do sistema operacional chama esse método, independentemente do ponto de entrada especificado no arquivo de imagem.  
  
 No Windows 98, Windows ME, Windows NT e Windows 2000, o `_CorExeMain` função é chamada indiretamente por meio de um ajuste no carregador do sistema operacional. Em todas as outras versões do Windows, ele é chamado diretamente pelo carregador do sistema operacional.  
  
 Para obter mais informações, consulte a seção comentários a [CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) tópico.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Funções estáticas globais de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
