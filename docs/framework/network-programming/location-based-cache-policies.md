---
title: "Políticas de cache baseadas na localização"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Cache If Available policy
- reload policy
- location-based cache policies
- Cache Only policy
- local cache
- intermediate cache
- No Cache No Store policy
- cache [.NET Framework], location-based policies
- Revalidate policy
- freshness of cached resources
- Cache Or Next Cache Only policy
- Refresh policy
ms.assetid: e41d7f1a-0a6a-4dee-97d1-c6a8b6a07fc2
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: a09c8c47c91222d6292d46d2eea80a30ed786494
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="location-based-cache-policies"></a>Políticas de cache baseadas na localização
Uma política de cache baseada na localização define a atualização das entradas armazenadas em cache válidas de acordo com o local em que o recurso solicitado pode ser obtido. Um recurso em cache é válido se usá-lo não viola os requisitos de revalidação especificados pelo servidor. Uma política de cache baseada na localização é criada programaticamente usando um construtor de classe <xref:System.Net.Cache.RequestCachePolicy> ou <xref:System.Net.Cache.HttpRequestCachePolicy>. O tipo de política baseada na localização é passado para o construtor usando um valor de enumeração <xref:System.Net.Cache.RequestCacheLevel> ou <xref:System.Net.Cache.HttpRequestCacheLevel>. Para obter exemplos de código que criam políticas de cache baseadas na localização, consulte [Como definir uma política de cache baseada na localização para um aplicativo](../../../docs/framework/network-programming/how-to-set-a-location-based-cache-policy-for-an-application.md). As seções a seguir explicam cada tipo de política de cache baseada na localização para recursos de protocolo HTTP (http e https).  
  
## <a name="cache-if-available-policy"></a>Política de armazenar em cache se disponível  
 Se um recurso solicitado válido estiver no cache local, o recurso armazenado em cache será usado; caso contrário, a solicitação para o recurso será enviada ao servidor. Se o recurso solicitado estiver disponível em qualquer cache entre o cliente e o servidor, a solicitação poderá ser atendida por um cache intermediário.  
  
## <a name="cache-only-policy"></a>Política de somente cache  
 Se um recurso solicitado válido estiver no cache local, o recurso armazenado em cache será usado. Ao se especificar esse nível de política de cache, uma exceção <xref:System.Net.WebException> será lançada se o item não estiver no cache local.  
  
## <a name="cache-or-next-cache-only-policy"></a>Política de somente cache ou próximo cache  
 Se um recurso solicitado válido está no cache local ou em um cache intermediário na rede local, o recurso armazenado em cache é usado. Se não, uma exceção é lançada de <xref:System.Net.WebException> . No protocolo de cache HTTP, isso é feito usando a diretiva de controle de cache somente se armazenado em cache.  
  
## <a name="no-cache-no-store-policy"></a>Política sem cache, sem repositório  
 Um recurso solicitado nunca é usado de nenhum cache e nunca é colocado em nenhum cache. Se um recurso solicitado estiver presente no cache local, ele será removido. Esse nível de política indica aos caches intermediários que eles também devem remover o recurso. No protocolo de cache HTTP, isso é feito usando a diretiva de controle de cache sem repositório.  
  
## <a name="refresh-policy"></a>Política de atualizar  
 Um recurso solicitado pode ser usado se for obtido do servidor ou localizado em um cache que não seja o cache local. Antes de a solicitação poder ser atendida por um cache intermediário, esse cache deve revalidar sua entrada armazenada em cache com o servidor. No protocolo de cache HTTP, isso é feito usando a diretiva de controle de cache max-age = 0 no cabeçalho Pragma sem cache.  
  
## <a name="reload-policy"></a>Política de recarregar  
 Os recursos solicitados devem ser obtidos do servidor. A resposta pode ser salva no cache local. No protocolo de cache HTTP, isso é feito usando a diretiva de controle de cache sem cache e o cabeçalho Pragma sem cache.  
  
## <a name="revalidate-policy"></a>Política de revalidar  
 Compara a cópia do recurso no cache com a cópia no servidor. Se a cópia no servidor for mais recente, ela será usada para atender à solicitação e substituirá a cópia em cache. Se a cópia em cache for igual à cópia do servidor, a cópia armazenada em cache será usada. No protocolo de cache HTTP, isso é feito usando uma solicitação condicional.  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciamento de cache para aplicativos de rede](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Política de cache](../../../docs/framework/network-programming/cache-policy.md)  
 [Políticas de cache baseadas em tempo](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [Configurando o cache em aplicativos de rede](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [\<requestCaching> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md) [Elemento requestCaching> (configurações de rede)]
