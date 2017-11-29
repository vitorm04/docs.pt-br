---
title: Code-behind e XAML no WPF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 241fe815f1a7c2e70a664068a47d511a3dbd7e0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="code-behind-and-xaml-in-wpf"></a>Code-behind e XAML no WPF
<a name="introduction"></a> Code-behind é um termo usado para descrever o código unido a objetos definidos com marcação quando uma página [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é compilada com marcação. Este tópico descreve os requisitos para code-behind, bem como um mecanismo de código embutido alternativo para o código em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Esse tópico contém as seguintes seções:  
  
-   [Pré-requisitos](#Prerequisites)  
  
-   [Code-Behind e a linguagem XAML](#codebehind_and_the_xaml_language)  
  
-   [Code-behind, manipulador de eventos e requisitos de classe parcial no WPF](#Code_behind__Event_Handler__and_Partial_Class)  
  
-   [x:Code](#x_Code)  
  
-   [Limitações de código embutido](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Este tópico pressupõe que você tenha lido a [Visão geral da linguagem XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) e tenha algum conhecimento básico sobre o [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] e a programação orientada a objeto.  
  
<a name="codebehind_and_the_xaml_language"></a>   
## <a name="code-behind-and-the-xaml-language"></a>Code-Behind e a linguagem XAML  
 A linguagem XAML inclui recursos de nível de linguagem que tornam possível associar arquivos de código com arquivos de marcação, do lado do arquivo de marcação. Especificamente, a linguagem XAML define os recursos de linguagem [Diretiva x:Class](../../../../docs/framework/xaml-services/x-class-directive.md), [Diretiva x:Subclass](../../../../docs/framework/xaml-services/x-subclass-directive.md) e [Diretiva x:ClassModifier](../../../../docs/framework/xaml-services/x-classmodifier-directive.md). O modo exato como o código deve ser produzido e como a marcação e o código devem ser integrados não faz parte do que a linguagem XAML especifica. É deixado para as estruturas, como o WPF, determinarem como integrar o código, como usar a linguagem XAML nos modelos de aplicativo e programação e as ações de build ou outros tipos de suporte que são exigidos.  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>Code-behind, manipulador de eventos e requisitos de classe parcial no WPF  
  
-   A classe parcial deve derivar do tipo que sustenta o elemento raiz.  
  
-   Observe que, sob o comportamento padrão das ações de build de compilação de marcação, você pode deixar a derivação em branco na definição de classe parcial no lado da lógica. O resultado compilado assumirá o tipo de suporte da raiz da página para ser a base para a classe parcial, mesmo se não for especificado. No entanto, contar com esse comportamento não é uma prática recomendada.  
  
-   Os manipuladores de eventos que você escreve no code-behind devem ser métodos de instância e não podem ser métodos estáticos. Esses métodos devem ser definidos pela classe parcial dentro do namespace CLR identificado por `x:Class`. Você não pode qualificar o nome de um manipulador de eventos para instruir um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para procurar por um manipulador de eventos para fiação de evento em um escopo de classe diferente.  
  
-   O manipulador deve corresponder ao delegado para o evento apropriado no sistema de tipo de suporte.  
  
-   Para o idioma [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] especificamente, você pode usar a palavra-chave `Handles` específico a um idioma para associar manipuladores com instâncias e eventos na declaração do manipulador, em vez de anexar manipuladores com atributos em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. No entanto, essa técnica tem algumas limitações, uma vez que a palavra-chave `Handles` não pode dar suporte a todos os recursos específicos do sistema de eventos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], como determinados cenários de evento roteado ou eventos anexados. Para obter detalhes, consulte [Visual Basic e manipulação de eventos WPF](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
<a name="x_Code"></a>   
## <a name="xcode"></a>x:Code  
 [X:Code](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md) é um elemento de diretiva definido em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Um elemento de diretiva `x:Code` pode conter um código de programação embutido. O código que é definido como embutido pode interagir com o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] na mesma página. O exemplo a seguir ilustra o código [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] embutido. Observe que o código está dentro do elemento `x:Code` e que ele deve ser cercado por `<CDATA[`... `]]>` para liberar o conteúdo de [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], de modo que um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (interpretando o esquema [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ou o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]) não tentará interpretar o conteúdo literalmente como [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)].  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## <a name="inline-code-limitations"></a>Limitações de código embutido  
 Considere evitar ou limitar o uso de código embutido. Em termos de arquitetura e filosofia de código, manter uma separação entre a marcação e o code-behind mantém as funções de designer e de desenvolvedor muito mais distintas. Em um nível mais técnico, o código que você escreve para o código embutido pode ser complicado de escrever, porque você está sempre escrevendo na classe parcial [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] gerada e só pode usar os mapeamentos de namespace de XML padrão. Uma vez que não é possível adicionar instruções `using`, você deverá qualificar totalmente muitas das chamadas [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] realizadas. Os mapeamentos padrão de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] incluem a maioria dos namespaces [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] que estão presentes nos assemblies [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], mas não todos; você terá que qualificar completamente as chamadas para tipos e membros contidos dentro de outros namespaces CLR. Você também não poderá definir nada além da classe parcial no código embutido e todas as entidades de código de usuário que você referencia devem existir como um membro ou uma variável na classe parcial gerada. Outros recursos específicos da linguagem de programação, como as macros ou `#ifdef` contra as variáveis globais ou de build, também não estão disponíveis. Para obter mais informações, consulte [x:Code Intrinsic XAML Type](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md) (Tipo intrínseco x:Code (XAML)).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Tipo intrínseco x:Code (XAML)](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md)  
 [Compilar um aplicativo WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [Sintaxe XAML em detalhes](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
