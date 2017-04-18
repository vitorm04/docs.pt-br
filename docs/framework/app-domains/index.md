---
title: "Programação com domínios de aplicativos e assemblies | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: c50b3e328998b65ec47efe6d7457b36116813c77
ms.openlocfilehash: 6078d7eafaad8f695c3ef5efd4a3cc37da7dee3c
ms.lasthandoff: 04/08/2017

---
# <a name="programming-with-application-domains-and-assemblies"></a>Programação com domínios do aplicativo e assemblies
Os hosts como Microsoft Internet Explorer, ASP.NET e o shell do Windows carregam o Common Language Runtime em um processo, criam um [domínio do aplicativo](../../../docs/framework/app-domains/application-domains.md) nesse processo e, em seguida, carregam e executam código de usuário nesse domínio do aplicativo ao executar um aplicativo .NET Framework. Na maioria dos casos, você não precisa se preocupar em criar domínios do aplicativo nem em carregar assemblies neles, pois o host de tempo de execução executa essas tarefas.  
  
 No entanto, se estiver criando um aplicativo que hospedará o Common Language Runtime, criando ferramentas ou código que deseja descarregar de modo programático, ou criando componentes conectáveis que podem ser descarregados e recarregados dinamicamente, você estará criando seus próprios domínios do aplicativo. Mesmo se não estiver criando um host de tempo de execução, esta seção fornece informações importantes sobre como trabalhar com domínios do aplicativo e assemblies carregados nesses domínios do aplicativo.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Tópicos explicativos sobre domínios do aplicativo e assemblies](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 Fornece links a todos os Tópicos explicativos encontrados na documentação conceitual para programação com domínios do aplicativo e assemblies.  
  
 [Usando domínios do aplicativo](../../../docs/framework/app-domains/use.md)  
 Fornece exemplos de como criar, configurar e usar domínios do aplicativo.  
  
 [Programação com assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 Descreve como criar, assinar e definir atributos em assemblies.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Emissão de métodos e assemblies dinâmicos](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 Descreve como criar assemblies dinâmicos.  
  
 [Assemblies no Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Fornece uma visão geral conceitual de assemblies.  
  
 [Domínios do aplicativo](../../../docs/framework/app-domains/application-domains.md)  
 Fornece uma visão geral conceitual de domínios de aplicativos.  
  
 [Visão geral da reflexão](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Descreve como usar a classe **Reflection** para obter informações sobre um assembly.
