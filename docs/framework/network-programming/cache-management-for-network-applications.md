---
title: Gerenciamento de cache para aplicativos de rede
ms.date: 03/30/2017
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c2b27f3516169ee7b90eaa27fbf22ec02fb638fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391671"
---
# <a name="cache-management-for-network-applications"></a>Gerenciamento de cache para aplicativos de rede
Este tópico e seus subtópicos relacionados descrevem o cache para recursos obtidos usando as classes <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest> e <xref:System.Net.FtpWebRequest>.  
  
 Um cache fornece armazenamento temporário de recursos que foram solicitados por um aplicativo. Se um aplicativo solicitar o mesmo recurso mais de uma vez, o recurso poderá ser retornado do cache, evitando a sobrecarga de solicitá-lo novamente ao servidor. O cache pode melhorar o desempenho do aplicativo reduzindo o tempo necessário para obter um recurso solicitado. O cache também pode diminuir o tráfego de rede reduzindo o número de viagens ao servidor. Embora o cache melhore o desempenho, ele aumenta o risco de que o recurso retornado para o aplicativo seja obsoleto, o que significa que ele não é idêntico ao recurso que seria enviado pelo servidor se o cache não estivesse em uso.  
  
 O cache pode permitir que usuários ou processos não autorizados leiam dados confidenciais. Uma resposta autenticada que é armazenada em cache pode ser recuperada do cache sem uma autorização adicional. Se o cache estiver habilitado, altere para <xref:System.Net.WebRequest.CachePolicy%2A>, <xref:System.Net.Cache.RequestCacheLevel.BypassCache> ou <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> para desabilitar o cache nessa solicitação.  
  
 Devido a preocupações de segurança, o cache **não** é recomendado para cenários de camada intermediária.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Política de cache](../../../docs/framework/network-programming/cache-policy.md)  
 Explica o que é uma política de cache e como definir uma.  
  
 [Políticas de cache baseadas na localização](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 Define cada tipo de política de cache baseada na localização disponível para os recursos do protocolo HTTP (http e https).  
  
 [Políticas de cache baseadas em tempo](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 Descreve os critérios que podem ser usados para personalizar uma política de cache baseada em tempo.  
  
 [Configurando o cache em aplicativos de rede](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 Descreve como criar políticas de cache e solicitações que usam o cache de forma programática.  
  
## <a name="reference"></a>Referência  
 <xref:System.Net.Cache>  
 Define os tipos e as enumerações usados para definir políticas de cache para os recursos obtidos usando as classes <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest> e <xref:System.Net.FtpWebRequest>.
