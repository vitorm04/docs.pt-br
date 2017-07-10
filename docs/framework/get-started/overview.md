---
title: "Visão geral do .NET Framework | Microsoft Docs"
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
- application development [.NET Framework]
- common language runtime
- common language runtime, about
- common language runtime, overview
ms.assetid: 29848c96-fc36-462d-8072-ba223a40b697
caps.latest.revision: 34
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: fe9ab371ab8d3eee3778412e446b7aa30b42476b
ms.openlocfilehash: f7af2ff5db3d6d06383906fc271ae60d68f43731
ms.contentlocale: pt-br
ms.lasthandoff: 05/19/2017

---
<a id="overview-of-the-net-framework" class="xliff"></a>
# Visão geral do .NET Framework
O .NET Framework é uma tecnologia que dá suporte à compilação e à execução da próxima geração de aplicativos e serviços Web XML. O .NET Framework foi criado para atender aos seguintes objetivos:  
  
-   Para fornecer um ambiente de programação orientada a objeto consistente, independentemente do código do objeto ser armazenado e executado localmente, executado localmente mas distribuído pela Internet ou executado remotamente.  
  
-   Para fornecer um ambiente de execução de código que minimize conflitos de implantação e criação de versão do software.  
  
-   Para fornecer um ambiente da execução que promova a execução segura do código, incluindo o código criado por terceiros desconhecidos ou semiconfiáveis.  
  
-   Para fornecer um ambiente de execução de código que elimine os problemas de desempenho dos ambientes interpretados ou com scripts.  
  
-   Para tornar a experiência do desenvolvedor consistente entre diversos tipos de aplicativos, como aplicativos baseados no Windows e aplicativos baseados na Web.  
  
-   Para compilar toda a comunicação segundo padrões do setor a fim de garantir que o código baseado no .NET Framework possa se integrar a qualquer outro código.  
  
> [!NOTE]
>  Para obter uma introdução geral ao .NET Framework para usuários e desenvolvedores, veja [Introdução](../../../docs/framework/get-started/index.md).  
  
 O .NET Framework consiste no Common Language Runtime e na biblioteca de classes .NET Framework. O Common Language Runtime é a base do .NET Framework. Você pode pensar no tempo de execução como um agente que gerencia o código no tempo de execução, fornecendo serviços básicos como gerenciamento de memória, gerenciamento de threads e comunicação remota, enquanto também impõe a segurança de tipos rígida e outras formas de precisão de código que promovam segurança e robustez. Na verdade, o conceito de gerenciamento de código é um princípio fundamental do tempo de execução. O código que segmenta o tempo de execução é conhecido como código gerenciado, e o código que não segmenta o tempo de execução é conhecido como código não gerenciado. A biblioteca de classes é uma coleção orientada a objeto de tipos reutilizáveis que você pode usar para desenvolver aplicativos, desde linhas de comando tradicionais ou aplicativos GUI (interface gráfica do usuário) a aplicativos com base nas inovações mais recentes fornecidas pelo ASP.NET, como Web Forms e Serviços Web XML.  
  
 O .NET Framework pode ser hospedado por componentes não gerenciados que carregam o Common Language Runtime em seus processos e iniciam a execução de código gerenciado, criando, assim, um ambiente de software que pode explorar recursos gerenciados e não gerenciados. O .NET Framework não apenas fornece vários hosts de tempo de execução, mas também dá suporte ao desenvolvimento de hosts de tempo de execução de terceiros.  
  
 Por exemplo, o ASP.NET hospeda o tempo de execução para fornecer um ambiente do servidor escalonável para código gerenciado. ASP.NET trabalha diretamente com o tempo de execução para habilitar aplicativos ASP.NET e serviços Web XML, e ambos serão discutidos mais adiante neste tópico.  
  
 Internet Explorer é um exemplo de um aplicativo não gerenciado que hospeda o tempo de execução (na forma de uma extensão tipo MIME). Usar o Internet Explorer para hospedar o tempo de execução permite que você insira componentes gerenciados ou controles Windows Forms em documentos HTML. Hospedar o tempo de execução dessa maneira torna possível o gerenciamento de código móvel, mas com melhorias significativas que somente o código gerenciado pode oferecer, como execução semiconfiável e armazenamento isolado de arquivos.  
  
 A ilustração a seguir mostra o relacionamento do Common Language Runtime e da biblioteca de classes com seus aplicativos e com o sistema geral. A ilustração também mostra como o código gerenciado opera dentro uma arquitetura maior.  
  
 ![Código gerenciado em uma arquitetura maior](../../../docs/framework/get-started/media/circle.gif "circle")  
.NET Framework em contexto  
  
 As seções a seguir descrevem os recursos principais do .NET Framework com mais detalhes.  
  
<a id="features-of-the-common-language-runtime" class="xliff"></a>
## Recursos do Common Language Runtime  
 O Common Language Runtime gerencia memória, execução de threads, execução de código, verificação de segurança do código, compilação e outros serviços do sistema. Esses recursos são intrínsecos ao código gerenciado, executado no Common Language Runtime.  
  
 Quanto à segurança, os componentes gerenciados recebem níveis de confiança variados, dependendo do número de fatores que incluem sua origem (como a Internet, a rede corporativa ou o computador local). Isso significa que um componente gerenciado pode ou não ser capaz de executar operações de acesso a arquivo, operações de acesso a Registro ou outras funções confidenciais, mesmo que esteja sendo usado no mesmo aplicativo ativo.  
  
 O tempo de execução impõe segurança de acesso ao código. Por exemplo, os usuários podem confiar que um executável inserido em uma página da Web possa executar uma animação na tela ou tocar uma música, mas não possa acessar seus dados pessoais, arquivos de sistema ou rede. Assim, os recursos de segurança do tempo de segurança permitem que o software implantado pela Internet legítimo seja excepcionalmente avançado.  
  
 O tempo de execução também impõe robustez ao código implementando uma infraestrutura rígida de verificação de tipo e código chamada CTS (Common Type System). O CTS assegura que todo código gerenciado seja autodescritivo. Os diversos compiladores de linguagem da Microsoft e de terceiros geram códigos gerenciados de acordo com o CTS. Isso significa que o código gerenciado pode consumir outros tipos e instâncias gerenciados, enquanto impõem rigorosamente a fidelidade e a segurança do tipo.  
  
 Além disso, o ambiente gerenciado do tempo de execução elimina muitos problemas de software comuns. Por exemplo, o tempo de execução identifica automaticamente o layout do objeto e gerencia referências a eles, liberando-os quando não estão mais sendo usados. Esse gerenciamento de memória automático resolve os dois erros mais comuns de aplicativo: perdas e referências de memória inválidas.  
  
 O tempo de execução também aumenta a produtividade do desenvolvedor. Por exemplo, os programadores podem escrever aplicativos em sua linguagem de desenvolvimento preferida, mas aproveitar todo o tempo de execução, a biblioteca de classes e os componentes escritos em outras linguagens por outros desenvolvedores. Qualquer fornecedor de compilador que optar por segmentar o tempo de execução pode fazê-lo. Compiladores de linguagem que segmentam o .NET Framework disponibilizam os recursos do .NET Framework para códigos existentes, escritos nessa linguagem, facilitando bastante o processo de migração para aplicativos existentes.  
  
 Embora tenha sido criado para o software do futuro, o tempo de execução também dá suporte ao software de hoje e de amanhã. Interoperabilidade entre códigos gerenciados e não gerenciados permite que os desenvolvedores continuem usando os componentes COM e DLLs necessários.  
  
 O tempo de execução foi projetado para melhorar o desempenho. Embora o Common Language Runtime forneça vários serviços de tempo de execução padrão, o código gerenciado jamais é interpretado. Um recurso chamado compilação JIT (just-in-time) permite que todos os códigos gerenciados sejam executados na linguagem de máquina nativa do sistema, na qual está em execução. Enquanto isso, o gerenciador de memória remove as possibilidades de memória fragmentada e aumenta a localidade de referência da memória, melhorando ainda mais o desempenho.  
  
 Por fim, o tempo de execução pode ser hospedado por aplicativos do servidor de alto desempenho, como o Microsoft SQL Server e o IIS (Serviços de Informações da Internet). Essa infraestrutura permite que você use código gerenciado para escrever sua lógica de negócio, enquanto aproveita o desempenho superior dos melhores servidores de empresa que dão suporte à hospedagem em tempo de execução.  
  
<a id="net-framework-class-library" class="xliff"></a>
## Biblioteca de classes .NET Framework  
 A biblioteca de classes .NET Framework é uma coleção de tipos reutilizáveis que se integram plenamente ao Common Language Runtime. A biblioteca de classes é orientada a objeto, fornecendo tipos que seu próprio código gerenciado pode derivar. Isso não apenas torna os tipos do .NET Framework fáceis de usar, mas também reduz o tempo associado ao aprendizado de novos recursos do .NET Framework. Além disso, componentes de terceiros podem ser totalmente integrados a classes do .NET Framework.  
  
 Por exemplo, as classes da coleção do .NET Framework implementam um conjunto de interfaces que você pode usar para desenvolver suas próprias coleções de classes. Sua coleção de classes será perfeitamente combinada às classes do .NET Framework.  
  
 Como você esperaria de uma biblioteca de classes orientada a objeto, os tipos do .NET Framework permitem que você realize várias tarefas de programação comuns, incluindo tarefas como gerenciamento da cadeia de caracteres, coleta de dados, conectividade de banco de dados e acesso a arquivos. Além dessas tarefas comuns, a biblioteca de classes inclui tipos que dão suporte a vários cenários de desenvolvimento especializados. Por exemplo, você pode usar o .NET Framework para desenvolver os seguintes tipos de aplicativos e serviços:  
  
-   Aplicativos de console. Confira [Compilação de aplicativos de console](../../../docs/standard/building-console-apps.md).  
  
-   Aplicativos GUI do Windows (Windows Forms). Confira [Windows Forms](../../../docs/framework/winforms/index.md).  
  
-   Aplicativos Windows Presentation Foundation (WPF). Confira [Windows Presentation Foundation](../../../docs/framework/wpf/index.md).  
  
-   Aplicativos do ASP.NET. Confira [Aplicativos Web com o ASP.NET](../../../docs/framework/develop-web-apps-with-aspnet.md).  
  
-   Serviços do Windows. Confira [Introdução a aplicativos do Serviço Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md).  
  
-   Aplicativos orientados a serviço usando o Windows Communication Foundation (WCF). Confira [Aplicativos orientados a serviço com WCF](../../../docs/framework/wcf/index.md).  
  
-   Aplicativos habilitados para fluxo de trabalho usando o Windows Workflow Foundation (WF). Confira [Compilação de fluxos de trabalho no .NET Framework](http://msdn.microsoft.com/en-us/cbf3880f-dc7b-466d-b808-1109b1223f4a).  
  
 Por exemplo, as classes Windows Forms são um conjunto abrangente de tipos reutilizáveis que simplificam muito o desenvolvimento de GUI Windows. Se criar um aplicativo Web Form do ASP.NET, você poderá usar as classes Web Forms.  
  
<a id="see-also" class="xliff"></a>
## Consulte também  
 [Requisitos de sistema](../../../docs/framework/get-started/system-requirements.md)   
 [Guia de instalação](../../../docs/framework/install/index.md)   
 [Guia de desenvolvimento](../../../docs/framework/development-guide.md)   
 [ Ferramentas](../../../docs/framework/tools/index.md)   
 [Exemplos do .NET Framework](http://msdn.microsoft.com/en-us/177055f8-4a1f-43e7-aee6-995c196079b1)   
 [Biblioteca de classes .NET Framework](http://go.microsoft.com/fwlink/?LinkID=227195)
