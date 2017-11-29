---
title: "Usando domínios do aplicativo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 53180d5d3d9314c3f078ddca8f5c155b01981f4e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="using-application-domains"></a>Usando domínios do aplicativo
Os domínios do aplicativos fornecem uma unidade de isolamento para o Common Language Runtime. Eles são criados e executados dentro de um processo. Domínios do aplicativo geralmente são criados por um host de tempo de execução, que é um aplicativo responsável por carregar o tempo de execução para um processo e executar o código do usuário em um domínio do aplicativo. O host de tempo de execução cria um processo e um domínio de aplicativo padrão e executa o código gerenciado dentro dele. Hosts de tempo de execução incluem ASP.NET, Microsoft Internet Explorer e o shell do Windows.  
  
 Para a maioria dos aplicativos, você não precisará criar seu próprio domínio do aplicativo; o host de tempo de execução cria os domínios do aplicativo necessários para você. No entanto, você pode criar e configurar domínios do aplicativo adicionais se seu aplicativo precisar isolar o código ou usar e descarregar DLLs.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como criar um domínio do aplicativo](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 Descreve como criar um domínio do aplicativo com programação.  
  
 [Como descarregar um domínio do aplicativo](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 Descreve como descarregar um domínio do aplicativo com programação.  
  
 [Como configurar um domínio do aplicativo](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 Fornece uma introdução à configuração de um domínio do aplicativo.  
  
 [Recuperação de informações de instalação de um domínio do aplicativo](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 Descreve como recuperar informações de configuração de um domínio do aplicativo.  
  
 [Como carregar assemblies em um domínio do aplicativo](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 Descreve como carregar um assembly em um domínio do aplicativo.  
  
 [Como obter as informações de tipo e membro de um assembly](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 Descreve como recuperar informações sobre um assembly.  
  
 [Cópias de sombra de assemblies](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 Descreve como a cópia de sombra permite realizar atualizações nos assemblies enquanto eles estão em uso e como configurar cópias de sombra.  
  
 [Como receber notificações de exceção de primeira tentativa](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 Explica como você pode receber uma notificação de que uma exceção foi gerada, antes do Common Language Runtime começar a procurar por manipuladores de exceção.  
  
 [Como resolver carregamentos de assembly](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 Fornece diretrizes sobre como usar o evento <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> para resolver falhas de carregamento de assembly.  
  
## <a name="reference"></a>Referência  
 <xref:System.AppDomain>  
 Representa um domínio do aplicativo. Fornece métodos para criar e controlar domínios de aplicativo.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Assemblies no Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Fornece uma visão geral das funções executadas por assemblies.  
  
 [Programação com assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 Descreve como criar, assinar e definir atributos em assemblies.  
  
 [Emissão de métodos e assemblies dinâmicos](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 Descreve como criar assemblies dinâmicos.  
  
 [Domínios do aplicativo](../../../docs/framework/app-domains/application-domains.md)  
 Fornece uma visão geral conceitual de domínios de aplicativos.  
  
 [Visão geral da reflexão](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Descreve como usar a classe **Reflection** para obter informações sobre um assembly.
