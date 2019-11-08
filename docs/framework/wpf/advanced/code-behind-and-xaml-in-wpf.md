---
title: Code-behind e XAML no WPF
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: c18cce1898b8834c20d5e4af70c1b010e4b96e11
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740906"
---
# <a name="code-behind-and-xaml-in-wpf"></a>Code-behind e XAML no WPF
<a name="introduction"></a> Code-behind é um termo usado para descrever o código unido a objetos definidos com marcação quando uma página [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é compilada com marcação. Este tópico descreve os requisitos para code-behind, bem como um mecanismo de código embutido alternativo para o código em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Esse tópico contém as seguintes seções:  
  
- [Pré-requisitos](#Prerequisites)  
  
- [Code-Behind e a linguagem XAML](#codebehind_and_the_xaml_language)  
  
- [Code-behind, manipulador de eventos e requisitos de classe parcial no WPF](#Code_behind__Event_Handler__and_Partial_Class)  
  
- [x:Code](#x_Code)  
  
- [Limitações de código embutido](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Prerequisites  
 Este tópico pressupõe que você leu a [visão geral do XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) e tem algum conhecimento básico do CLR e da programação orientada a objeto.  
  
<a name="codebehind_and_the_xaml_language"></a>   
## <a name="code-behind-and-the-xaml-language"></a>Code-Behind e a linguagem XAML  
 A linguagem XAML inclui recursos de nível de linguagem que tornam possível associar arquivos de código com arquivos de marcação, do lado do arquivo de marcação. Especificamente, a linguagem XAML define os recursos de linguagem [Diretiva x:Class](../../xaml-services/x-class-directive.md), [Diretiva x:Subclass](../../xaml-services/x-subclass-directive.md) e [Diretiva x:ClassModifier](../../xaml-services/x-classmodifier-directive.md). O modo exato como o código deve ser produzido e como a marcação e o código devem ser integrados não faz parte do que a linguagem XAML especifica. É deixado para as estruturas, como o WPF, determinarem como integrar o código, como usar a linguagem XAML nos modelos de aplicativo e programação e as ações de build ou outros tipos de suporte que são exigidos.  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>Code-behind, manipulador de eventos e requisitos de classe parcial no WPF  
  
- A classe parcial deve derivar do tipo que sustenta o elemento raiz.  
  
- Observe que, sob o comportamento padrão das ações de build de compilação de marcação, você pode deixar a derivação em branco na definição de classe parcial no lado da lógica. O resultado compilado assumirá o tipo de suporte da raiz da página para ser a base para a classe parcial, mesmo se não for especificado. No entanto, contar com esse comportamento não é uma prática recomendada.  
  
- Os manipuladores de eventos que você escreve no code-behind devem ser métodos de instância e não podem ser métodos estáticos. Esses métodos devem ser definidos pela classe parcial dentro do namespace CLR identificado por `x:Class`. Você não pode qualificar o nome de um manipulador de eventos para instruir um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para procurar por um manipulador de eventos para fiação de evento em um escopo de classe diferente.  
  
- O manipulador deve corresponder ao delegado para o evento apropriado no sistema de tipo de suporte.  
  
- Para a linguagem Microsoft Visual Basic especificamente, você pode usar a palavra-chave `Handles` específica do idioma para associar manipuladores com instâncias e eventos na declaração do manipulador, em vez de anexar manipuladores com atributos em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. No entanto, essa técnica tem algumas limitações, uma vez que a palavra-chave `Handles` não pode dar suporte a todos os recursos específicos do sistema de eventos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], como determinados cenários de evento roteado ou eventos anexados. Para obter detalhes, consulte [Visual Basic e manipulação de eventos WPF](visual-basic-and-wpf-event-handling.md).  
  
<a name="x_Code"></a>   
## <a name="xcode"></a>x:Code  
 [X:Code](../../xaml-services/x-code-intrinsic-xaml-type.md) é um elemento de diretiva definido em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Um elemento de diretiva `x:Code` pode conter um código de programação embutido. O código que é definido como embutido pode interagir com o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] na mesma página. O exemplo a seguir ilustra C# o código embutido. Observe que o código está dentro do elemento `x:Code` e que o código deve ser circundado por `<CDATA[`...`]]>` para escapar o conteúdo de XML, de forma que um processador de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (interpretando o esquema [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ou o esquema de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]) não tente interprete o conteúdo literalmente como XML.  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## <a name="inline-code-limitations"></a>Limitações de código embutido  
 Considere evitar ou limitar o uso de código embutido. Em termos de arquitetura e filosofia de código, manter uma separação entre a marcação e o code-behind mantém as funções de designer e de desenvolvedor muito mais distintas. Em um nível mais técnico, o código que você escreve para o código embutido pode ser complicado de escrever, porque você está sempre escrevendo na classe parcial [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] gerada e só pode usar os mapeamentos de namespace de XML padrão. Como não é possível adicionar `using` instruções, você deve qualificar totalmente muitas das chamadas de API que você faz. Os mapeamentos de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] padrão incluem a maioria dos namespaces CLR que estão presentes nos assemblies de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]; Você terá que qualificar totalmente as chamadas para tipos e membros contidos nos outros namespaces CLR. Você também não poderá definir nada além da classe parcial no código embutido e todas as entidades de código de usuário que você referencia devem existir como um membro ou uma variável na classe parcial gerada. Outros recursos específicos da linguagem de programação, como as macros ou `#ifdef` contra as variáveis globais ou de build, também não estão disponíveis. Para obter mais informações, consulte [x:Code Intrinsic XAML Type](../../xaml-services/x-code-intrinsic-xaml-type.md) (Tipo intrínseco x:Code (XAML)).  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Tipo intrínseco x:Code (XAML)](../../xaml-services/x-code-intrinsic-xaml-type.md)
- [Compilar um aplicativo WPF](../app-development/building-a-wpf-application-wpf.md)
- [Sintaxe XAML em detalhes](xaml-syntax-in-detail.md)
