---
title: Tipos migrados do WPF para System.Xaml
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
caps.latest.revision: 14
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f4d4bc0b21770e5ac0c138c140334198d30a740a
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>Tipos migrados do WPF para System.Xaml
Em [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] e [!INCLUDE[net_v30_long](../../../includes/net-v30-long-md.md)], ambos [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] e Windows Workflow Foundation incluída uma implementação de linguagem XAML. Muitos dos tipos públicos que forneceu a extensibilidade para a implementação do WPF XAML existiam no assembly WindowsBase PresentationCore e PresentationFramework. Da mesma forma, os tipos públicos que é fornecida a extensibilidade de XAML do Windows Workflow Foundation existiam no assembly System.Workflow.ComponentModel. No [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], alguns dos tipos relacionados a XAML são migradas para o assembly System. XAML. Uma implementação comum do .NET Framework dos serviços de linguagem XAML permite muitos cenários de extensibilidade XAML que foram originalmente definidos pela implementação de XAML de uma estrutura específica, mas agora fazem parte do total [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] suporte de linguagem XAML. Este tópico lista os tipos que são migrados e aborda os problemas relacionados à migração.  
  
<a name="assemblies_and_namespaces"></a>   
## <a name="assemblies-and-namespaces"></a>Assemblies e Namespaces  
 Em [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] e [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], os tipos de WPF implementado para dar suporte a XAML foram geralmente no <xref:System.Windows.Markup> namespace. A maioria desses tipos foram no assembly WindowsBase.  
  
 Em [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], há uma nova <xref:System.Xaml> namespace e um novo assembly System. XAML. Muitos dos tipos que foram implementados originalmente para WPF XAML agora são fornecidos como pontos de extensibilidade ou serviços para qualquer implementação do XAML. Como parte do disponibilizando-as para cenários mais gerais, os tipos são tipo encaminhado do seu assembly WPF original para o assembly System. XAML. Isso possibilita cenários de extensibilidade XAML sem a necessidade de incluir os assemblies de outras estruturas (como WPF e Windows Workflow Foundation).  
  
 Para tipos migrados, a maioria dos tipos de permanecem na <xref:System.Windows.Markup> namespace. Isso foi parcialmente evitar que os mapeamentos de namespace CLR em implementações existentes em uma base por arquivo. Como resultado, o <xref:System.Windows.Markup> namespace em [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] contém uma mistura de tipos gerais de suporte de linguagem XAML (do assembly System. XAML) e tipos que são específicos para a implementação do WPF XAML (de WindowsBase e outros assemblies WPF). Qualquer tipo que foi migrado para System. XAML, mas existia anteriormente em um assembly do WPF, tem suporte ao encaminhamento de tipo na versão 4 do assembly WPF.  
  
### <a name="workflow-xaml-support-types"></a>Tipos de suporte do fluxo de trabalho XAML  
 Windows Workflow Foundation também fornecido tipos de suporte XAML, e em muitos casos, esses tinham idênticos nomes curtos para um equivalente do WPF. A seguir está uma lista dos tipos de suporte do Windows Workflow Foundation XAML:  
  
-   <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>  
  
-   <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>  
  
-   <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>  
  
 Esses tipos ainda existem nos assemblies do Windows Workflow Foundation para o suporte [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] e ainda pode ser usado para aplicativos específicos do Windows Workflow Foundation; no entanto, eles não devem ser referenciados por aplicativos ou estruturas que não usam O Windows Workflow Foundation.  
  
<a name="markupextension"></a>   
## <a name="markupextension"></a>MarkupExtension  
 No [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] e [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], o <xref:System.Windows.Markup.MarkupExtension> classe no assembly WindowsBase para WPF. Uma classe paralela para Windows Workflow Foundation, <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>, existente no assembly System.Workflow.ComponentModel. No [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], o <xref:System.Windows.Markup.MarkupExtension> classe é migrada para o assembly System. XAML. No [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], <xref:System.Windows.Markup.MarkupExtension> destina-se para qualquer cenário de extensibilidade XAML que usa serviços de XAML .NET Framework, não apenas para aqueles que se baseiam em estruturas específicas. Quando possível, estruturas específicas ou código do usuário no framework também deve criar <xref:System.Windows.Markup.MarkupExtension> classe para a extensão do XAML.  
  
<a name="markupextension_supporting_service_classes"></a>   
## <a name="markupextension-supporting-service-classes"></a>Classes de serviço de MarkupExtension com suporte  
 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] e [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] para WPF fornecidas vários serviços que estavam disponíveis para <xref:System.Windows.Markup.MarkupExtension> implementadores e <xref:System.ComponentModel.TypeConverter> implementações para dar suporte ao uso de propriedade do tipo em XAML. Esses serviços são os seguintes:  
  
-   <xref:System.Windows.Markup.IProvideValueTarget>  
  
-   <xref:System.Windows.Markup.IUriContext>  
  
-   <xref:System.Windows.Markup.IXamlTypeResolver>  
  
> [!NOTE]
>  Outro serviço de [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] que está relacionado a extensões de marcação é o <xref:System.Windows.Markup.IReceiveMarkupExtension> interface. <xref:System.Windows.Markup.IReceiveMarkupExtension> não foi migrada e está marcado como `[Obsolete]` para [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. Cenários que usava <xref:System.Windows.Markup.IReceiveMarkupExtension> deve usar <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> atribuído retornos de chamada. <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> também é marcado como `[Obsolete]`.  
  
<a name="xaml_language_features"></a>   
## <a name="xaml-language-features"></a>Recursos de linguagem XAML  
 Vários recursos de linguagem XAML e componentes para WPF já existiam no assembly PresentationFramework. Eles foram implementados como um <xref:System.Windows.Markup.MarkupExtension> subclasse para expor os usos de extensão de marcação na marcação XAML. No [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], estes existem no assembly System. XAML para que os projetos que não têm os assemblies do WPF podem usar esses recursos de nível de linguagem XAML. O WPF usa essas mesmas implementações para [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] aplicativos. Como com outros casos listados neste tópico, os tipos de suporte continuam existindo no <xref:System.Windows.Markup> namespace para evitar que referências anteriores.  
  
 A tabela a seguir contém uma lista das classes de suporte a recursos de XAML que são definidas em System. XAML.  
  
|Recurso de linguagem XAML|Uso|  
|---------------------------|-----------|  
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|  
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|  
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|  
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|  
  
 Embora System. XAML não pode ter classes específicas de suporte, a lógica geral de recursos de idioma para a linguagem XAML de processamento agora reside no System. XAML e seus leitores XAML implementados e gravadores XAML. Por exemplo, `x:TypeArguments` é um atributo que é processado por leitores XAML e autores de XAML de implementações de System. XAML; ele pode ser observado no fluxo do nó XAML, tem tratamento no contexto de esquema padrão XAML (baseado em CLR), tem um sistema de tipo XAML representação e assim por diante. Como resultado, a documentação de referência para todos os recursos de nível de linguagem XAML é um subtópico para [serviços XAML](../../../docs/framework/xaml-services/index.md) e área geral do conjunto de documentação do .NET Framework, em vez de ser parte da documentação do WPF definida como um subtópico [avançado (Windows Presentation Foundation)](../../../docs/framework/wpf/advanced/index.md) (como ainda é o caso em conjuntos de documentação 3.5).  
  
<a name="valueserializer_and_supporting_classes"></a>   
## <a name="valueserializer-and-supporting-classes"></a>ValueSerializer e Classes de suporte  
 O <xref:System.Windows.Markup.ValueSerializer> classe dá suporte à conversão de tipo em uma cadeia de caracteres, especialmente para casos de serialização de XAML que serialização pode exigir vários modos ou nós na saída. Em [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] e [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], o <xref:System.Windows.Markup.ValueSerializer> para WPF no assembly WindowsBase. No [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], o <xref:System.Windows.Markup.ValueSerializer> classe está em System. XAML e destina-se para qualquer cenário de extensibilidade XAML, não apenas para aqueles que se baseiam no WPF. <xref:System.Windows.Markup.IValueSerializerContext> (um serviço de suporte) e <xref:System.Windows.Markup.DateTimeValueSerializer> (uma subclasse específica) também são migradas para System. XAML.  
  
<a name="xamlrelated_attributes"></a>   
## <a name="xaml-related-attributes"></a>Atributos de XAML  
 WPF XAML incluídos vários atributos que podem ser aplicados a tipos CLR para indicar algo sobre seu comportamento XAML. A seguir está uma lista dos atributos que existiam em assemblies do WPF no [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] e [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]. Esses atributos são migrados para System. XAML no [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
-   <xref:System.Windows.Markup.AmbientAttribute>  
  
-   <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
-   <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
-   <xref:System.Windows.Markup.DependsOnAttribute>  
  
-   <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
-   <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
-   <xref:System.Windows.Markup.RootNamespaceAttribute>  
  
-   <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
-   <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
-   <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
-   <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
-   <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
-   <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
-   <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
-   <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
<a name="miscellaneous_classes"></a>   
## <a name="miscellaneous-classes"></a>Classes de diversos  
 O <xref:System.Windows.Markup.IComponentConnector> interface existia no WindowsBase no [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] e [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], mas existe em System. XAML no [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. <xref:System.Windows.Markup.IComponentConnector> é usado principalmente para ferramentas de suporte e compiladores de marcação XAML.  
  
 O <xref:System.Windows.Markup.INameScope> interface existia no WindowsBase no [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] e [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], mas existe em System. XAML no [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. <xref:System.Windows.Markup.INameScope> Define as operações básicas para um namescope XAML.  
  
<a name="xamlrelated_classes_with_shared_names_that_exist_in_wpf_and_systemxaml"></a>   
## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>Classes relacionadas a XAML com nomes compartilhados que existem no WPF e System. XAML  
 As seguintes classes existem os assemblies do WPF e o assembly System. XAML no [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]:  
  
 `XamlReader`  
  
 `XamlWriter`  
  
 `XamlParseException`  
  
 A implementação do WPF foi encontrada no <xref:System.Windows.Markup> namespace e assembly PresentationFramework. A implementação de System. XAML é encontrada no <xref:System.Xaml> namespace. Se você estiver usando tipos de WPF ou é derivados de tipos do WPF, você normalmente deve usar as implementações de WPF de <xref:System.Windows.Markup.XamlReader> e <xref:System.Windows.Markup.XamlWriter> em vez das implementações de System. XAML. Para obter mais informações, consulte comentários em <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> e <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>.  
  
 Se você está incluindo referências a assemblies do WPF e System. XAML, e você também estiver usando `include` instruções para ambos os <xref:System.Windows.Markup> e <xref:System.Xaml> namespaces, talvez você precise qualificar totalmente as chamadas para essas APIs para resolver os tipos sem ambiguidade.  
  
## <a name="see-also"></a>Consulte também  
 [Serviços XAML](../../../docs/framework/xaml-services/index.md)
