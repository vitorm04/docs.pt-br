---
title: '&lt;relativeBindForResources&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ffd5b62e0759b3a4f97e105e884912a41f0117de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltrelativebindforresourcesgt-element"></a>&lt;relativeBindForResources&gt; elemento
Otimiza o teste para assemblies satélites.  
  
 \<Configuração > elemento  
\<tempo de execução > elemento  
\<relativeBindForResources > elemento  
  
## <a name="syntax"></a>Sintaxe  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se o common language runtime otimiza o teste para assemblies satélite.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|O tempo de execução não otimiza o teste para assemblies satélite. Este é o valor padrão.|  
|`true`|O tempo de execução otimiza a investigação de assemblies de satélite.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do tempo de execução.|  
  
## <a name="remarks"></a>Comentários  
 Em geral, o Gerenciador de recursos de testes para recursos, conforme documentado no [Empacotando e implantando recursos](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) tópico. Isso significa que quando o Gerenciador de recursos de testes para uma determinada versão localizada de um recurso, ele pode pesquisar no cache de assembly global, pesquisar em uma pasta específica da cultura na consulta do aplicativo de base, de código do Windows Installer para assemblies satélite e gerar o <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> evento. O `<relativeBindForResources>` elemento otimiza a maneira na qual o Gerenciador de recursos sondas para assemblies satélite. Ela pode melhorar o desempenho quando a investigação de recursos sob as seguintes condições:  
  
-   Quando o assembly satélite é implantado no mesmo local que o assembly de código. Em outras palavras, se o assembly de código estiver instalado no cache de assembly global, os assemblies satélites também devem ser instalados existe. Se o assembly de código estiver instalado na base de código do aplicativo, os assemblies satélites também devem ser instalados em uma pasta específica da cultura na base de código.  
  
-   Quando o Windows Installer não é usado ou apenas raramente é usado para a instalação sob demanda de assemblies de satélite.  
  
-   Quando o código do aplicativo não tratar o <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> evento.  
  
 Definindo o `enabled` atributo do `<relativeBindForResources>` elemento `true` otimiza a investigação do Gerenciador de recursos para assemblies de satélite da seguinte maneira:  
  
-   Ele usa o local do assembly de código pai para investigação para o assembly satélite.  
  
-   Ele não faz a consulta do Windows Installer para assemblies satélite.  
  
-   Ele não gere o <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> evento.  
  
## <a name="see-also"></a>Consulte também  
 [Empacotando e implantando recursos](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
 [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
