---
title: Tipos migrados do WPF para System.Xaml
ms.date: 03/30/2017
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
ms.openlocfilehash: 37433768c1bca3c013fb1e505d55bd7295f34933
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758022"
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>Tipos migrados do WPF para System.Xaml
No .NET Framework 3.5 e .NET Framework 3.0, ambos [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] e Windows Workflow Foundation incluído uma implementação de linguagem XAML. Muitos dos tipos públicos que forneceu a extensibilidade para a implementação de XAML WPF existiam nos assemblies PresentationFramework, PresentationCore e WindowsBase. Da mesma forma, os tipos públicos que forneceu a extensibilidade para Windows Workflow Foundation XAML existiam no assembly ComponentModel. No .NET Framework 4, alguns dos tipos relacionados a XAML são migradas para o assembly System. XAML. Uma implementação comum do .NET Framework dos serviços de linguagem XAML habilita muitos cenários de extensibilidade XAML que foram originalmente definidos pela implementação de XAML de uma estrutura específica, mas que agora fazem parte do suporte de linguagem XAML do .NET Framework 4 geral. Este tópico lista os tipos que são migrados e aborda questões relacionadas à migração.  
  
<a name="assemblies_and_namespaces"></a>   
## <a name="assemblies-and-namespaces"></a>Assemblies e Namespaces  
 No .NET Framework 3.5 e .NET Framework 3.0, os tipos de WPF implementado para dar suporte a XAML eram geralmente no <xref:System.Windows.Markup> namespace. A maioria desses tipos foi no assembly WindowsBase.  
  
 No .NET Framework 4, há uma nova <xref:System.Xaml> namespace e um novo assembly System. XAML. Muitos dos tipos que foram originalmente implementados para XAML WPF agora são fornecidos como pontos de extensibilidade ou serviços para qualquer implementação de XAML. Como parte de torná-las disponíveis para cenários mais gerais, os tipos são encaminhados por tipo de seu assembly original do WPF ao assembly System. XAML. Isso permite cenários de extensibilidade XAML sem ter que inclua os assemblies de outras estruturas (por exemplo, WPF e Windows Workflow Foundation).  
  
 Para tipos migrados, a maioria dos tipos de permanecer no <xref:System.Windows.Markup> namespace. Isso foi parcialmente evitar a interrupção de mapeamentos de namespace CLR em implementações existentes em uma base por arquivo. Como resultado, o <xref:System.Windows.Markup> namespace no .NET Framework 4 contém uma mistura de tipos gerais de suporte de linguagem XAML (do assembly System. XAML) e tipos que são específicos para a implementação de WPF XAML (de WindowsBase e outros assemblies WPF). Qualquer tipo que foi migrado para System. XAML, mas existia anteriormente em um assembly do WPF, tem suporte ao encaminhamento de tipo na versão 4 do assembly do WPF.  
  
### <a name="workflow-xaml-support-types"></a>Tipos de suporte do fluxo de trabalho XAML  
 Windows Workflow Foundation também forneceu deem suporte a tipos XAML e, em muitos casos eles tinham nomes curtos idêntico a um WPF equivalente. A seguir está uma lista dos tipos de suporte do Windows Workflow Foundation XAML:  
  
- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>  
  
 Esses suporte tipos, ainda existem nos assemblies do Windows Workflow Foundation para o .NET Framework 4 e ainda podem ser usado para aplicativos específicos do Windows Workflow Foundation; No entanto, eles não devem ser referenciados por aplicativos ou estruturas que não usam o Windows Workflow Foundation.  
  
<a name="markupextension"></a>   
## <a name="markupextension"></a>MarkupExtension  
 No .NET Framework 3.5 e .NET Framework 3.0, o <xref:System.Windows.Markup.MarkupExtension> de classe para o WPF foi no assembly WindowsBase. Uma classe parallel for Windows Workflow Foundation, <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>, existente no assembly ComponentModel. No .NET Framework 4, o <xref:System.Windows.Markup.MarkupExtension> classe é migrado para o assembly System. XAML. No .NET Framework 4, <xref:System.Windows.Markup.MarkupExtension> destina-se para qualquer cenário de extensibilidade XAML que usa serviços de XAML .NET Framework, não apenas para aqueles que se baseiam em estruturas específicas. Quando possível, estruturas específicas ou código do usuário no framework também deve criar <xref:System.Windows.Markup.MarkupExtension> classe para a extensão do XAML.  
  
<a name="markupextension_supporting_service_classes"></a>   
## <a name="markupextension-supporting-service-classes"></a>MarkupExtension que dão suporte a Classes de serviço  
 .NET framework 3.5 e .NET Framework 3.0 para o WPF fornecidos vários serviços que estavam disponíveis para <xref:System.Windows.Markup.MarkupExtension> implementadores e <xref:System.ComponentModel.TypeConverter> implementações para dar suporte ao uso de tipo ou propriedade em XAML. Esses serviços são os seguintes:  
  
- <xref:System.Windows.Markup.IProvideValueTarget>  
  
- <xref:System.Windows.Markup.IUriContext>  
  
- <xref:System.Windows.Markup.IXamlTypeResolver>  
  
> [!NOTE]
>  Outro serviço do .NET Framework 3.5 que está relacionado às extensões de marcação é o <xref:System.Windows.Markup.IReceiveMarkupExtension> interface. <xref:System.Windows.Markup.IReceiveMarkupExtension> não foi migrada e está marcado como `[Obsolete]` para o .NET Framework 4. Cenários que usava <xref:System.Windows.Markup.IReceiveMarkupExtension> em vez disso, deve usar <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> atribuído retornos de chamada. <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> também é marcado `[Obsolete]`.  
  
<a name="xaml_language_features"></a>   
## <a name="xaml-language-features"></a>Recursos da linguagem XAML  
 Vários recursos de linguagem XAML e componentes do WPF existiam anteriormente no assembly PresentationFramework. Eles foram implementados como um <xref:System.Windows.Markup.MarkupExtension> subclasse para expor os usos de extensão de marcação na marcação XAML. No .NET Framework 4, eles existem no assembly System. XAML para que os projetos que não incluem assemblies WPF podem usar esses recursos de nível de linguagem XAML. O WPF usa essas implementações mesmas para aplicativos do .NET Framework 4. Como com outros casos listados neste tópico, os tipos de suporte continuam existindo no <xref:System.Windows.Markup> namespace para evitar a interrupção de referências anteriores.  
  
 A tabela a seguir contém uma lista das classes de suporte a recursos de XAML que são definidos em System. XAML.  
  
|Recurso de linguagem XAML|Uso|  
|---------------------------|-----------|  
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|  
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|  
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|  
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|  
  
 Embora a System. XAML não pode ter classes de suporte específico, a lógica geral para o processamento de recursos de linguagem para a linguagem XAML agora reside em System. XAML e seu implementados leitores XAML e gravadores XAML. Por exemplo, `x:TypeArguments` é um atributo que é processado por leitores XAML e gravadores XAML de implementações de System. XAML; ele pode ser observado no fluxo de nó XAML, tem tratamento no contexto de esquema XAML (baseado em CLR) padrão, tem um sistema de tipos XAML representação e assim por diante. Como resultado, a documentação de referência para todos os recursos de nível de linguagem XAML é um subtópico para [serviços de XAML](index.md) e nessa área geral do conjunto de documentação do .NET Framework, em vez de ser parte da documentação do WPF definida como um subtópico [avançado (Windows Presentation Foundation)](../wpf/advanced/index.md) (como ainda é o caso em conjuntos de documentação 3.5).  
  
<a name="valueserializer_and_supporting_classes"></a>   
## <a name="valueserializer-and-supporting-classes"></a>ValueSerializer e dar suporte a Classes  
 O <xref:System.Windows.Markup.ValueSerializer> classe dá suporte à conversão de tipo em uma cadeia de caracteres, particularmente para casos de serialização de XAML em que a serialização pode exigir vários modos ou nós na saída. No .NET Framework 3.5 e .NET Framework 3.0, o <xref:System.Windows.Markup.ValueSerializer> para WPF foi no assembly WindowsBase. No .NET Framework 4, o <xref:System.Windows.Markup.ValueSerializer> classe está em System. XAML e destina-se para qualquer cenário de extensibilidade XAML, não apenas para aqueles que se baseiam em WPF. <xref:System.Windows.Markup.IValueSerializerContext> (um serviço de suporte) e <xref:System.Windows.Markup.DateTimeValueSerializer> (uma subclasse específica) também são migradas para System. XAML.  
  
<a name="xamlrelated_attributes"></a>   
## <a name="xaml-related-attributes"></a>Atributos relacionados ao XAML  
 XAML WPF incluído vários atributos que podem ser aplicados a tipos CLR para indicar algo sobre seu comportamento XAML. O exemplo a seguir é uma lista dos atributos que existiam em assemblies do WPF no .NET Framework 3.5 e .NET Framework 3.0. Esses atributos são migrados para o System. XAML no .NET Framework 4.  
  
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
  
<a name="miscellaneous_classes"></a>   
## <a name="miscellaneous-classes"></a>Diversas Classes  
 O <xref:System.Windows.Markup.IComponentConnector> interface existiu em WindowsBase no .NET Framework 3.5 e .NET Framework 3.0, mas existe em System. XAML no .NET Framework 4. <xref:System.Windows.Markup.IComponentConnector> serve basicamente para as ferramentas de suporte e compiladores de marcação XAML.  
  
 O <xref:System.Windows.Markup.INameScope> interface existiu em WindowsBase no .NET Framework 3.5 e .NET Framework 3.0, mas existe em System. XAML no .NET Framework 4. <xref:System.Windows.Markup.INameScope> Define as operações básicas de um namescope XAML.  
  
<a name="xamlrelated_classes_with_shared_names_that_exist_in_wpf_and_systemxaml"></a>   
## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>Classes relacionadas a XAML com nomes compartilhados que existem no WPF e System. XAML  
 As classes a seguir existem em assemblies WPF e o assembly System. XAML no .NET Framework 4:  
  
 `XamlReader`  
  
 `XamlWriter`  
  
 `XamlParseException`  
  
 A implementação do WPF é encontrada no <xref:System.Windows.Markup> namespace e o assembly PresentationFramework. A implementação de System. XAML é encontrada no <xref:System.Xaml> namespace. Se você estiver usando tipos WPF ou estiver derivando de tipos do WPF, você normalmente deve usar as implementações WPF <xref:System.Windows.Markup.XamlReader> e <xref:System.Windows.Markup.XamlWriter> em vez das implementações de System. XAML. Para obter mais informações, consulte os comentários no <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> e <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>.  
  
 Se você está incluindo referências a assemblies WPF e System. XAML, e você também estiver usando `include` instruções para ambos os <xref:System.Windows.Markup> e <xref:System.Xaml> namespaces, talvez você precise qualificar totalmente as chamadas para essas APIs para resolver os tipos sem ambiguidade.  
  
## <a name="see-also"></a>Consulte também

- [Serviços XAML](index.md)
