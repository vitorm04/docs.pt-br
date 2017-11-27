---
title: Coclass CorpubPublish
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorpubPublish Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CorpubPublish
helpviewer_keywords: CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3c1565c9321e64536139e02b239fbeb4247a58a3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="corpubpublish-coclass"></a>Coclass CorpubPublish
Fornece interfaces para publicar as informações sobre domínios de aplicativos e processos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a>Interfaces  
  
|Interface|Descrição|  
|---------------|-----------------|  
|[Interface ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|Fornece métodos para publicar as informações sobre processos e os domínios de aplicativo nesses processos.|  
|[Interface ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|Representa e fornece informações sobre um domínio de aplicativo em um processo.|  
|[Interface ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|Fornece métodos que atravessam uma coleção de domínios de aplicativo que existem dentro de um processo.|  
|[Interface ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|Representa um processo que está em execução em um computador.|  
|[Interface ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|Fornece métodos que atravessam uma coleção de processos em execução em um computador.|  
  
## <a name="remarks"></a>Comentários  
 Um cenário típico de publicação envolve um desenvolvedor que deseja depurar código gerenciado que está em execução em um computador em um domínio de aplicativo. O ambiente de hospedagem pode estar executando mais de um domínio de aplicativo dentro de um processo. O desenvolvedor gostaria de usar uma interface gráfica do usuário ou outros meios para listar todos os processos que estão em execução no computador e selecione um processo específico. A listagem deve incluir todos os domínios de aplicativo dentro de processos que estão executando o código gerenciado. O desenvolvedor pode, em seguida, identificar o domínio de aplicativo específico e anexar um depurador ao domínio.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorPub.idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
