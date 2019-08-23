---
title: Tipos migrados do WPF para System.Xaml
ms.date: 03/30/2017
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
ms.openlocfilehash: 943cdb2a21cbf2f95ef7fe2feefe6c0e71f57be4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939676"
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>Tipos migrados do WPF para System.Xaml
No .NET Framework 3,5 e .NET Framework 3,0, tanto [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] o quanto o Windows Workflow Foundation incluíam uma implementação de linguagem XAML. Muitos dos tipos públicos que forneceram extensibilidade para a implementação XAML do WPF existiam nos assemblies WindowsBase, PresentationCore e PresentationFramework. Da mesma forma, os tipos públicos que forneceram extensibilidade para Windows Workflow Foundation XAML existiam no assembly System. Workflow. ComponentModel. No .NET Framework 4, alguns dos tipos relacionados a XAML são migrados para o assembly System. XAML. Uma implementação comum de .NET Framework de serviços de linguagem XAML permite muitos cenários de extensibilidade XAML que foram originalmente definidos por uma implementação de XAML de uma estrutura específica, mas que agora fazem parte do suporte geral a quatro idiomas XAML .NET Framework. Este tópico lista os tipos que são migrados e discute os problemas relacionados à migração.  
  
<a name="assemblies_and_namespaces"></a>   
## <a name="assemblies-and-namespaces"></a>Assemblies e namespaces  
 No .NET Framework 3,5 e .NET Framework 3,0, os tipos que o WPF implementou para oferecer suporte a XAML <xref:System.Windows.Markup> estavam geralmente no namespace. A maioria desses tipos estava no assembly WindowsBase.  
  
 No .NET Framework 4, há um novo <xref:System.Xaml> namespace e um novo assembly System. XAML. Muitos dos tipos que foram originalmente implementados para o WPF XAML agora são fornecidos como pontos de extensibilidade ou serviços para qualquer implementação do XAML. Como parte de torná-los disponíveis para cenários mais gerais, os tipos são encaminhados de tipo de seu assembly original do WPF para o assembly System. XAML. Isso permite cenários de extensibilidade XAML sem a necessidade de incluir os assemblies de outras estruturas (como WPF e Windows Workflow Foundation).  
  
 Para tipos migrados, a maioria dos tipos permanece no <xref:System.Windows.Markup> namespace. Isso foi parcial para evitar a interrupção dos mapeamentos de namespace CLR em implementações existentes por arquivo. Como resultado, o <xref:System.Windows.Markup> namespace no .NET Framework 4 contém uma mistura de tipos gerais de suporte a idiomas XAML (do assembly System. XAML) e tipos que são específicos para a implementação XAML do WPF (de WindowsBase e outros assemblies do WPF). Qualquer tipo que foi migrado para System. XAML, mas existia anteriormente em um assembly do WPF, tem suporte de encaminhamento de tipo na versão 4 do assembly do WPF.  
  
### <a name="workflow-xaml-support-types"></a>Tipos de suporte do fluxo de trabalho XAML  
 Windows Workflow Foundation também forneceu tipos de suporte XAML e, em muitos casos, eles tinham nomes curtos idênticos para um equivalente do WPF. A seguir está uma lista de tipos de suporte do Windows Workflow Foundation XAML:  
  
- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>  
  
 Esses tipos de suporte ainda existem nos assemblies de Windows Workflow Foundation para .NET Framework 4 e ainda podem ser usados para aplicativos Windows Workflow Foundation específicos; no entanto, eles não devem ser referenciados por aplicativos ou estruturas que não usam Windows Workflow Foundation.  
  
<a name="markupextension"></a>   
## <a name="markupextension"></a>MarkupExtension  
 No .NET Framework 3,5 e .NET Framework 3,0, a classe <xref:System.Windows.Markup.MarkupExtension> para o WPF estava no assembly WindowsBase. Uma classe paralela para Windows Workflow Foundation, <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>, existia no assembly System. Workflow. ComponentModel. No .NET Framework 4, a <xref:System.Windows.Markup.MarkupExtension> classe é migrada para o assembly System. XAML. No .NET Framework 4, <xref:System.Windows.Markup.MarkupExtension> destina-se a qualquer cenário de extensibilidade XAML que usa .NET Framework serviços XAML, não apenas para aqueles que se baseiam em estruturas específicas. Quando possível, estruturas específicas ou código de usuário na estrutura também devem criar a classe para <xref:System.Windows.Markup.MarkupExtension> a extensão XAML.  
  
<a name="markupextension_supporting_service_classes"></a>   
## <a name="markupextension-supporting-service-classes"></a>Classes de serviço de suporte MarkupExtension  
 .NET Framework 3,5 e .NET Framework 3,0 para o WPF forneciam vários serviços que estavam <xref:System.Windows.Markup.MarkupExtension> disponíveis para implementadores e <xref:System.ComponentModel.TypeConverter> implementações para dar suporte ao uso de tipo/propriedade em XAML. Esses serviços são os seguintes:  
  
- <xref:System.Windows.Markup.IProvideValueTarget>  
  
- <xref:System.Windows.Markup.IUriContext>  
  
- <xref:System.Windows.Markup.IXamlTypeResolver>  
  
> [!NOTE]
> Outro serviço do .NET Framework 3,5 relacionado a extensões de marcação é a <xref:System.Windows.Markup.IReceiveMarkupExtension> interface. <xref:System.Windows.Markup.IReceiveMarkupExtension>Não foi migrado e está marcado `[Obsolete]` para .NET Framework 4. Os cenários usados <xref:System.Windows.Markup.IReceiveMarkupExtension> anteriormente devem usar <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> os retornos de chamada atribuídos. <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute>também está marcado `[Obsolete]`.  
  
<a name="xaml_language_features"></a>   
## <a name="xaml-language-features"></a>Recursos de linguagem XAML  
 Vários recursos e componentes de linguagem XAML para WPF existiam anteriormente no assembly PresentationFramework. Elas foram implementadas como <xref:System.Windows.Markup.MarkupExtension> uma subclasse para expor usos de extensão de marcação na marcação XAML. No .NET Framework 4, eles existem no assembly System. XAML para que os projetos que não incluem assemblies do WPF possam usar esses recursos de nível de linguagem XAML. O WPF usa essas mesmas implementações para .NET Framework 4 aplicativos. Assim como nos outros casos listados neste tópico, os tipos de suporte continuam a existir no <xref:System.Windows.Markup> namespace para evitar a quebra de referências anteriores.  
  
 A tabela a seguir contém uma lista das classes de suporte de recurso XAML que são definidas em System. XAML.  
  
|Recurso de linguagem XAML|Uso|  
|---------------------------|-----------|  
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|  
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|  
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|  
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|  
  
 Embora System. XAML possa não ter classes de suporte específicas, a lógica geral para o processamento de recursos de linguagem para a linguagem XAML agora reside em System. XAML e seus leitores XAML e gravadores XAML. Por exemplo, `x:TypeArguments` é um atributo que é processado por leitores XAML e gravadores de XAML de implementações de System. XAML; ele pode ser observado no fluxo do nó XAML, manipulando no contexto de esquema XAML padrão (baseado em CLR), tem um tipo XAML-System representação e assim por diante. Como resultado, a documentação de referência para todos os recursos de nível de linguagem XAML é um subtópico para [serviços XAML](index.md) e essa área geral do conjunto de documentação .NET Framework, em vez de fazer parte do conjunto de documentação do WPF como um subtópico de [avançado ( Windows Presentation Foundation)](../wpf/advanced/index.md) (como ainda é o caso em conjuntos de documentação 3,5).  
  
<a name="valueserializer_and_supporting_classes"></a>   
## <a name="valueserializer-and-supporting-classes"></a>ValueSerializer não e classes de suporte  
 A <xref:System.Windows.Markup.ValueSerializer> classe dá suporte à conversão de tipo para uma cadeia de caracteres, particularmente para casos de serialização XAML em que a serialização pode exigir vários modos ou nós na saída. No .NET Framework 3,5 e .NET Framework 3,0, o <xref:System.Windows.Markup.ValueSerializer> para WPF estava no assembly WindowsBase. No .NET Framework 4, a classe <xref:System.Windows.Markup.ValueSerializer> está em System. XAML e destina-se a qualquer cenário de extensibilidade XAML, não apenas para aqueles que se baseiam no WPF. <xref:System.Windows.Markup.IValueSerializerContext>(um serviço de suporte) <xref:System.Windows.Markup.DateTimeValueSerializer> e (uma subclasse específica) também são migrados para System. XAML.  
  
<a name="xamlrelated_attributes"></a>   
## <a name="xaml-related-attributes"></a>Atributos relacionados a XAML  
 O WPF XAML incluía vários atributos que podem ser aplicados a tipos CLR para indicar algo sobre seu comportamento XAML. A seguir está uma lista dos atributos que existiam em assemblies do WPF no .NET Framework 3,5 e .NET Framework 3,0. Esses atributos são migrados para System. XAML no .NET Framework 4.  
  
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
## <a name="miscellaneous-classes"></a>Classes diversas  
 A <xref:System.Windows.Markup.IComponentConnector> interface existia em WindowsBase no .NET Framework 3,5 e .NET Framework 3,0, mas existe em System. XAML no .NET Framework 4. <xref:System.Windows.Markup.IComponentConnector>destina-se principalmente a ferramentas de suporte e compiladores de marcação XAML.  
  
 A <xref:System.Windows.Markup.INameScope> interface existia em WindowsBase no .NET Framework 3,5 e .NET Framework 3,0, mas existe em System. XAML no .NET Framework 4. <xref:System.Windows.Markup.INameScope>define operações básicas para um namescope XAML.  
  
<a name="xamlrelated_classes_with_shared_names_that_exist_in_wpf_and_systemxaml"></a>   
## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>Classes relacionadas a XAML com nomes compartilhados que existem no WPF e System. XAML  
 As classes a seguir existem nos assemblies do WPF e no assembly System. XAML no .NET Framework 4:  
  
 `XamlReader`  
  
 `XamlWriter`  
  
 `XamlParseException`  
  
 A implementação do WPF é encontrada no <xref:System.Windows.Markup> namespace e no assembly PresentationFramework. A implementação de System. XAML é encontrada no <xref:System.Xaml> namespace. Se você estiver usando tipos do WPF ou estiver derivando de tipos do WPF, normalmente deverá usar as implementações <xref:System.Windows.Markup.XamlReader> do <xref:System.Windows.Markup.XamlWriter> WPF de e em vez das implementações de System. XAML. Para obter mais informações, consulte comentários <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> em <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>e.  
  
 Se você estiver incluindo referências para ambos os assemblies do WPF e System. XAML, e também estiver `include` usando instruções para os <xref:System.Windows.Markup> namespaces e <xref:System.Xaml> , talvez seja necessário qualificar totalmente as chamadas para essas APIs a fim de resolver os tipos sem ambigüidade.  
  
## <a name="see-also"></a>Consulte também

- [Serviços XAML](index.md)
