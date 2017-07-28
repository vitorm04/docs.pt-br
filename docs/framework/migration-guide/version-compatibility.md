---
title: "Compatibilidade de versão no .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework 4.5, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
caps.latest.revision: 35
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 741c2d1c49f44a6a7b299845cdc37cc8425c326b
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="version-compatibility-in-the-net-framework"></a>Compatibilidade de versão no .NET Framework
Compatibilidade com versões anteriores significa que um aplicativo desenvolvido para uma versão específica de uma plataforma será executado em versões posteriores dessa plataforma. O .NET Framework tenta maximizar a compatibilidade com versões anteriores: o código-fonte gravado para uma versão do .NET Framework deve compilar em versões posteriores do .NET Framework e os binários executados em uma versão do .NET Framework devem se comportar de forma idêntica em versões posteriores do .NET Framework.  
  
<a name="Apps"></a>   
## <a name="version-compatibility-for-apps"></a>Compatibilidade de versão para aplicativos  
 Por padrão, um aplicativo executado na versão do .NET Framework para o qual foi compilado. Se essa versão não estiver presente e o arquivo de configuração do aplicativo não definir versões compatíveis, um erro de inicialização do .NET Framework poderá ocorrer. Nesse caso, a tentativa de executar o aplicativo falhará.  
  
 Para definir as versões específicas nas quais seu aplicativo é executado, adicione um ou mais elementos [\<supportedRuntime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) ao arquivo de configuração de aplicativo. Cada elemento `<supportedRuntime>` lista uma versão compatível do tempo de execução, com o primeiro especificando a versão mais preferida e o último especificando a versão menos preferida.  
  
```xml  
<configuration>  
   <startup>  
      <supportedRuntime version="v2.0.50727" />  
      <supportedRuntime version="v4.0" />  
   </startup>  
</configuration>  
```  
  
 Para saber mais, confira [How to: Configure an App to Support .NET Framework 4 or 4.x](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md) (Como configurar um aplicativo para dar suporte ao .NET Framework 4 ou 4.x).  
  
## <a name="version-compatibility-for-components"></a>Compatibilidade de versão para componentes  
 Um aplicativo pode controlar a versão do .NET Framework no qual é executado, mas um componente não pode. Os componentes e as bibliotecas de classe são carregados no contexto de um aplicativo específico e, assim, executados automaticamente na versão do .NET Framework em que o aplicativo é executado.  
  
 Por conta dessa restrição, as garantias de compatibilidade são especialmente importante para componentes. Desde o .NET Framework 4, você pode especificar o grau em que um componente deve permanecer compatível em várias versões aplicando o atributo <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=fullName> ao componente. As ferramentas podem usar esse atributo para detectar potenciais violações da garantia de compatibilidade em futuras versões de um componente.  
  
## <a name="backward-compatibility-and-the-net-framework-45"></a>Compatibilidade com versões anteriores e o .NET Framework 4.5  
 O .NET Framework 4.5 e suas versões pontuais (4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2 e 4.7) são compatíveis com versões anteriores de aplicativos que foram compilados com versões anteriores do .NET Framework. Em outras palavras, aplicativos e componentes compilados com versões anteriores funcionarão sem modificação no .NET Framework 4.5. No entanto, por padrão, como os aplicativos são executados na versão do Common Language Runtime para a qual foram desenvolvidos, você talvez tenha que fornecer um arquivo de configuração para permitir que seu aplicativo seja executado no .NET Framework 4.5. Para saber mais, confira a seção [Compatibilidade de versão para aplicativos](#Apps), anteriormente neste artigo.  
  
 Na prática, essa compatibilidade pode ser desfeita por alterações aparentemente inconsequentes feitas no .NET Framework e por alterações em técnicas de programação. Por exemplo, as melhorias de desempenho no .NET Framework 4.5 podem expor uma condição de corrida que não ocorria em versões anteriores. Da mesma forma, o uso de um caminho codificado para assemblies do .NET Framework, a execução de uma comparação de igualdade com uma versão específica do .NET Framework e a obtenção do valor de um campo particular usando-se reflexão não são práticas compatíveis com versões anteriores. Além disso, cada versão do .NET Framework inclui correções de bug e mudanças relacionadas à segurança que podem afetar a compatibilidade de alguns aplicativos e componentes.  
  
 Se o aplicativo ou componente não funcionar conforme esperado no .NET Framework 4.5 (incluindo suas versões pontuais, o [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1, 4.6.2 ou 4.7) use as seguintes listas de verificação:  
  
-   Consulte esses tópicos para ver todas as alterações que podem afetar seu aplicativo e aplique a solução alternativa descrita:  
  
    -   [Problemas de migração do .NET Framework 4](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md)  
  
    -   [Compatibilidade de aplicativos na versão 4.5](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)  
  
    -   [Compatibilidade de aplicativos na versão 4.5.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)  
  
    -   [Compatibilidade de aplicativos na versão 4.5.2](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-2.md)  
  
    -   [Compatibilidade de aplicativos na versão 4.6](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6.md)  
  
    -   [Compatibilidade de aplicativos na versão 4.6.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)  
  
    -   [Compatibilidade de aplicativos na versão 4.6.2](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)  

    - [Compatibilidade de aplicativos na versão 4.7](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)
       
-   Se você tiver um aplicativo do .NET Framework 1.1, examine também estes tópicos:  
  
    -   [Alterações no .NET Framework 2.0](http://go.microsoft.com/fwlink/?LinkID=125263)  
  
    -   [Alterações no .NET Framework 3.5 SP1](http://go.microsoft.com/fwlink/?LinkId=186989)  
  
-   Se você estiver recompilando o código-fonte existente para ser executado no .NET Framework 4.5 ou suas versões pontuais, ou se estiver desenvolvendo uma nova versão de um aplicativo ou componente direcionado ao [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] de uma base de código-fonte existente, confira [O que está obsoleto na biblioteca de classes](../../../docs/framework/whats-new/whats-obsolete.md) para obter tipos e membros obsoletos e aplicar a solução alternativa descrita. (O código compilado anteriormente continuará sendo executado em tipos e membros marcados como obsoletos.)  
  
-   Se você determinar que uma alteração no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] interrompeu o seu aplicativo, confira [Esquema de configurações de tempo de execução](../../../docs/framework/configure-apps/file-schema/runtime/index.md) para determinar se é possível usar uma configuração de tempo de execução em seu arquivo de configuração de aplicativo para restaurar o comportamento anterior.  
  
-   Se você encontrar um problema que não esteja documentado, registre um bug no [Microsoft Connect](http://go.microsoft.com/fwlink/?LinkID=154815) e contate [netfxcf@microsoft.com](mailto:netfxcf@microsoft.com) com o número do bug.  
  
## <a name="compatibility-and-side-by-side-execution"></a>Compatibilidade e execução lado a lado  
 Se você não conseguir encontrar uma solução alternativa adequada para seu problema, lembre-se de que o .NET Framework 4.5 (ou uma de suas versões pontuais) é executado lado a lado com as versões 1.1, 2.0 e 3.5, além de ser uma atualização in-loco que substitui a versão 4. Para aplicativos que segmentam as versões 1.1, 2.0 e 3.5, é possível instalar a versão do .NET Framework adequada no computador de destino para executar o aplicativo em seu melhor ambiente. Para saber mais sobre a execução lado a lado, confira [Side-by-Side Execution](../../../docs/framework/deployment/side-by-side-execution.md) (Execução lado a lado).  
  
## <a name="see-also"></a>Consulte também  
 [Novidades](../../../docs/framework/whats-new/index.md)   
 [O que está obsoleto na biblioteca de classes](../../../docs/framework/whats-new/whats-obsolete.md)   
 [Compatibilidade de aplicativos](../../../docs/framework/migration-guide/application-compatibility.md)   
 [Política de ciclo de vida de suporte do Microsoft .NET Framework](http://go.microsoft.com/fwlink/p/?LinkId=248212)   
 [Problemas de migração do .NET Framework 4](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md)

