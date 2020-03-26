---
title: Tipos migrados do WPF para System.Xaml
ms.date: 03/30/2017
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
ms.openlocfilehash: 5aa2d8a39be47d9affb97c3b60e53c4722c63cce
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249798"
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>Tipos migraram do WPF para o System.Xaml

No .NET Framework 3.5 e no .NET Framework 3.0, tanto o Windows Presentation Foundation (WPF) quanto o Windows Workflow Foundation incluíram uma implementação de linguagem XAML. Muitos dos tipos públicos que forneceram extensibilidade para a implementação do WPF XAML existiam nos conjuntos WindowsBase, PresentationCore e PresentationFramework. Da mesma forma, os tipos públicos que forneciam extensibilidade para o Windows Workflow Foundation XAML existiam no conjunto System.Workflow.ComponentModel. No .NET Framework 4, alguns dos tipos relacionados ao XAML foram migrados para o conjunto System.Xaml. Uma implementação comum do .NET Framework de serviços de linguagem XAML permite muitos cenários de extensibilidade XAML que foram originalmente definidos pela implementação XAML de uma estrutura específica, mas agora fazem parte do suporte geral ao idioma .NET Framework 4 XAML. Este artigo lista os tipos que foram migrados e discute questões relacionadas à migração.

## <a name="assemblies-and-namespaces"></a>Montagens e Namespaces

No .NET Framework 3.5 e no .NET Framework 3.0, os tipos que <xref:System.Windows.Markup> o WPF implementou para suportar o XAML estavam geralmente no namespace. A maioria desses tipos estava no conjunto WindowsBase.

No .NET Framework 4, <xref:System.Xaml> há um novo namespace e um novo conjunto System.Xaml. Muitos dos tipos que foram originalmente implementados para O WPF XAML são agora fornecidos como pontos ou serviços de extensibilidade para qualquer implementação do XAML. Como parte de disponibilizá-los para cenários mais gerais, os tipos são encaminhados do seu conjunto WPF original para o conjunto System.Xaml. Isso permite cenários de extensibilidade XAML sem ter que incluir os conjuntos de outras estruturas (como WPF e Windows Workflow Foundation).

Para tipos migrados, a maioria <xref:System.Windows.Markup> dos tipos permanece no namespace. Isso foi parcialmente para evitar a quebra de mapeamentos de namespace da CLR em implementações existentes por arquivo. Como resultado, <xref:System.Windows.Markup> o namespace no .NET Framework 4 contém uma mistura de tipos gerais de suporte à linguagem XAML (do conjunto System.Xaml) e tipos específicos para a implementação do WPF XAML (do WindowsBase e outros conjuntos WPF). Qualquer tipo que foi migrado para system.Xaml, mas existiu anteriormente em um conjunto WPF, tem suporte de tipo de encaminhamento na versão 4 do conjunto WPF.

### <a name="workflow-xaml-support-types"></a>Tipos de suporte XAML do fluxo de trabalho

O Windows Workflow Foundation também forneceu tipos de suporte XAML, e em muitos casos estes tinham nomes curtos idênticos a um equivalente WPF. A seguir está uma lista dos tipos de suporte do Windows Workflow Foundation XAML:

- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>

- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>

- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>

Esses tipos de suporte ainda existem nos conjuntos do Windows Workflow Foundation para .NET Framework 4 e ainda podem ser usados para aplicativos específicos do Windows Workflow Foundation; no entanto, eles não devem ser referenciados por aplicativos ou frameworks que não usam o Windows Workflow Foundation.

## <a name="markupextension"></a>MarkupExtension

No .NET Framework 3.5 e .NET Framework <xref:System.Windows.Markup.MarkupExtension> 3.0, a classe para WPF estava no conjunto WindowsBase. Uma classe paralela para Windows <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>Workflow Foundation, existiu no conjunto System.Workflow.ComponentModel. No .NET Framework 4, a <xref:System.Windows.Markup.MarkupExtension> classe é migrada para o conjunto System.Xaml. No .NET Framework <xref:System.Windows.Markup.MarkupExtension> 4, destina-se a qualquer cenário de extensibilidade XAML que use Serviços .NET XAML, não apenas para aqueles que se baseiam em frameworks específicos. Quando possível, frameworks específicos ou código de usuário <xref:System.Windows.Markup.MarkupExtension> na estrutura também devem ser baseados na classe para extensão XAML.

## <a name="markupextension-supporting-service-classes"></a>Classe de serviço de suporte de extensão de markupextension

.NET Framework 3.5 e .NET Framework 3.0 para WPF <xref:System.Windows.Markup.MarkupExtension> forneceram <xref:System.ComponentModel.TypeConverter> vários serviços que estavam disponíveis para implementadores e implementações para suportar o uso de tipo/propriedade no XAML. Estes serviços são os seguintes:

- <xref:System.Windows.Markup.IProvideValueTarget>

- <xref:System.Windows.Markup.IUriContext>

- <xref:System.Windows.Markup.IXamlTypeResolver>

> [!NOTE]
> Outro serviço do .NET Framework 3.5 que está <xref:System.Windows.Markup.IReceiveMarkupExtension> relacionado às extensões de marcação é a interface. <xref:System.Windows.Markup.IReceiveMarkupExtension>não foi migrado `[Obsolete]` e está marcado para .NET Framework 4. Os cenários <xref:System.Windows.Markup.IReceiveMarkupExtension> usados <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> anteriormente devem, em vez disso, usar retornos de chamada atribuídos. <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute>também está `[Obsolete]`marcado .

## <a name="xaml-language-features"></a>Características da linguagem XAML

Vários recursos e componentes de linguagem XAML para WPF existiam anteriormente no conjunto PresentationFramework. Estes foram <xref:System.Windows.Markup.MarkupExtension> implementados como uma subclasse para expor os usos de extensão de marcação na marcação XAML. No .NET Framework 4, estes existem no conjunto System.Xaml para que projetos que não incluam conjuntos WPF possam usar esses recursos de nível de linguagem XAML. O WPF usa essas mesmas implementações para aplicativos .NET Framework 4. Assim como os outros casos listados neste tópico, os tipos <xref:System.Windows.Markup> de suporte continuam existindo no namespace para evitar quebrar referências anteriores.

A tabela a seguir contém uma lista das classes de suporte a recursos XAML definidas em System.Xaml.

|Recurso de linguagem XAML|Uso|
|---------------------------|-----------|
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|

Embora o System.Xaml possa não ter classes de suporte específicas, a lógica geral para processar recursos de linguagem para a língua XAML agora reside no System.Xaml e seus leitores XAML implementados e escritores XAML. Por exemplo, `x:TypeArguments` é um atributo que é processado por leitores XAML e escritores XAML a partir de implementações System.Xaml; ele pode ser notado no fluxo de nó XAML, tem manuseio no contexto padrão (esquema XAML baseado em CLR), tem uma representação de sistema de tipo XAML, e assim por diante. Como resultado, a documentação de referência para todos os recursos de nível de linguagem XAML é um subtópico para [serviços XAML](../../../desktop-wpf/xaml-services/index.md) no [Desktop Guide for Windows Presentation Foundation (WPF)](../../../desktop-wpf/overview/index.md).

## <a name="valueserializer-and-supporting-classes"></a>Classes de ValueSerializer e Suporte

A <xref:System.Windows.Markup.ValueSerializer> classe suporta a conversão de tipo para uma seqüência, particularmente para casos de serialização XAML onde a serialização pode exigir vários modos ou nós na saída. No .NET Framework 3.5 e no .NET Framework 3.0, o <xref:System.Windows.Markup.ValueSerializer> para WPF estava no conjunto WindowsBase. No .NET Framework 4, a <xref:System.Windows.Markup.ValueSerializer> classe está no System.Xaml e é destinada a qualquer cenário de extensibilidade XAML, não apenas para aqueles que se baseiam no WPF. <xref:System.Windows.Markup.IValueSerializerContext>(um serviço de <xref:System.Windows.Markup.DateTimeValueSerializer> suporte) e (uma subclasse específica) também são migrados para System.Xaml.

## <a name="xaml-related-attributes"></a>Atributos relacionados ao XAML

O WPF XAML incluiu vários atributos que podem ser aplicados aos tipos CLR para indicar algo sobre seu comportamento XAML. A seguir está uma lista dos atributos que existiam nas assembléias wpf no .NET Framework 3.5 e .NET Framework 3.0. Esses atributos são migrados para System.Xaml no .NET Framework 4.

- <xref:System.Windows.Markup.AmbientAttribute>

- <xref:System.Windows.Markup.ContentPropertyAttribute>

- <xref:System.Windows.Markup.ContentWrapperAttribute>

- <xref:System.Windows.Markup.DependsOnAttribute>

- <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>

- <xref:System.Windows.Markup.NameScopePropertyAttribute>

- <xref:System.Windows.Markup.RootNamespaceAttribute>

- <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>

- <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>

- <xref:System.Windows.Markup.ValueSerializerAttribute>

- <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>

- <xref:System.Windows.Markup.XmlLangPropertyAttribute>

- <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>

- <xref:System.Windows.Markup.XmlnsDefinitionAttribute>

- <xref:System.Windows.Markup.XmlnsPrefixAttribute>

## <a name="miscellaneous-classes"></a>Classes Diversas

A <xref:System.Windows.Markup.IComponentConnector> interface existia no WindowsBase em .NET Framework 3.5 e .NET Framework 3.0, mas existe no System.Xaml no .NET Framework 4. <xref:System.Windows.Markup.IComponentConnector>destina-se principalmente ao suporte a ferramentas e compiladores de marcação XAML.

A <xref:System.Windows.Markup.INameScope> interface existia no WindowsBase em .NET Framework 3.5 e .NET Framework 3.0, mas existe no System.Xaml no .NET Framework 4. <xref:System.Windows.Markup.INameScope>define operações básicas para um namescope XAML.

## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>Classes relacionadas ao XAML com nomes compartilhados que existem no WPF e no System.Xaml

Existem as seguintes classes nos conjuntos WPF e no conjunto System.Xaml no Framework .NET 4:

`XamlReader`

`XamlWriter`

`XamlParseException`

A implementação do WPF é encontrada no namespace e no <xref:System.Windows.Markup> conjunto PresentationFramework. A implementação system.xaml <xref:System.Xaml> é encontrada no namespace. Se você estiver usando tipos de WPF ou estiver derivando de tipos de <xref:System.Windows.Markup.XamlReader> <xref:System.Windows.Markup.XamlWriter> WPF, você normalmente deve usar as implementações do WPF e, em vez das implementações do System.Xaml. Para obter mais informações, <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>consulte Observações e .

Se você estiver incluindo referências a conjuntos WPF e System.Xaml, e também estiver usando `include` instruções para os <xref:System.Windows.Markup> espaços de nome e <xref:System.Xaml> ambos, você pode precisar qualificar totalmente as chamadas para essas APIs, a fim de resolver os tipos sem ambiguidade.
