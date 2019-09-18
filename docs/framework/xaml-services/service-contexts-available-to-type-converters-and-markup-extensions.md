---
title: Contextos de serviço disponíveis para conversores de tipo e extensões de marcação
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services how-to
ms.assetid: b4dad00f-03da-4579-a4e9-d8d72d2ccbce
ms.openlocfilehash: 0d4e274ad7b64820e74347908c08c7726e96bbe8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053840"
---
# <a name="service-contexts-available-to-type-converters-and-markup-extensions"></a>Contextos de serviço disponíveis para conversores de tipo e extensões de marcação
Os autores dos tipos que dão suporte aos usos de conversor de tipo e extensão de marcação devem geralmente ter informações contextuais sobre onde um uso está localizado na marcação ou na estrutura do gráfico de objetos ao redor. As informações podem ser necessárias para que o objeto fornecido seja instanciado corretamente ou para que as referências de objeto a objetos existentes no grafo do objeto possam ser feitas. Ao usar .NET Framework serviços XAML, o contexto que pode ser necessário é exposto como uma série de interfaces de serviço. O código de suporte do conversor de tipo ou extensão de marcação pode consultar um serviço usando um contexto de provedor de serviço que está <xref:System.Xaml.XamlObjectWriter> disponível e transmitido por meio de tipos ou relacionados. O contexto de esquema XAML está diretamente disponível por meio de um desses serviços. Este tópico descreve como acessar contextos de serviço de uma implementação de conversor de valor e lista os serviços normalmente disponíveis e suas funções.  
  
<a name="obtaining_services"></a>   
## <a name="obtaining-services"></a>Obtendo serviços  
 Como um implementador de um conversor de valor, muitas vezes você precisa ter acesso a algum tipo de contexto no qual o conversor de valor é aplicado. Esse contexto pode incluir informações como o contexto do esquema XAML ativo, o acesso ao sistema de mapeamento de tipos que o contexto do esquema XAML e o gravador de objeto XAML fornecem, e assim por diante. Os serviços disponíveis para uma extensão de marcação ou implementação de conversor de tipo são comunicados por meio de parâmetros de contexto que fazem parte da assinatura de cada método virtual. Em todos os casos, você <xref:System.IServiceProvider> implementou no contexto e pode chamar <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType> para solicitar um serviço.  
  
<a name="services_for_a_markup_extension"></a>   
## <a name="services-for-a-markup-extension"></a>Serviços para uma extensão de marcação  
 <xref:System.Windows.Markup.MarkupExtension>tem apenas um método virtual, <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>. O parâmetro `serviceProvider` de entrada é como os serviços são comunicados às implementações quando a extensão de marcação é chamada por um processador XAML. O pseudocódigo a seguir ilustra como uma implementação de extensão de marcação pode consultar serviços <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>em seu:  
  
```csharp  
public override object ProvideValue(IServiceProvider serviceProvider)  
{  
...  
    // Get the IXamlTypeResolver from the service provider  
    if (serviceProvider == null)  
    {  
        throw new ArgumentNullException("serviceProvider");  
    }  
    IXamlTypeResolver xamlTypeResolver = serviceProvider.GetService(typeof(IXamlTypeResolver)) as IXamlTypeResolver;  
    if (xamlTypeResolver == null)  
   {  
        throw new ArgumentException("IXamlTypeResolver"));  
    }  
...  
}  
```  
  
<a name="services_for_a_type_converter"></a>   
## <a name="services-for-a-type-converter"></a>Serviços para um conversor de tipo  
 <xref:System.ComponentModel.TypeConverter>tem quatro métodos virtuais que usam um contexto de serviço e que dão suporte a usos de XAML. Cada um desses métodos passa um parâmetro `context` de entrada. Esse parâmetro é do tipo <xref:System.ComponentModel.ITypeDescriptorContext>, mas essa interface herda <xref:System.IServiceProvider>e, portanto, há um <xref:System.IServiceProvider.GetService%2A> método disponível para implementações do conversor de tipo.  
  
 O pseudocódigo a seguir ilustra como uma implementação de conversor de tipo para usos XAML pode consultar serviços em uma de suas substituições, neste <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>caso:  
  
```csharp  
public override object ConvertFrom(ITypeDescriptorContext typeDescriptorContext,  
  CultureInfo cultureInfo,  
  object source)  
{  
    IRootObjectProvider rootProvider = typeDescriptorContext.GetService(typeof(IRootObjectProvider)) as IRootObjectProvider;  
    if (rootProvider != null && source is String)  
    {  
        //return something, else ...  
    }  
    throw GetConvertFromException(source);  
}  
```  
  
<a name="services_for_a_value_serializer"></a>   
## <a name="services-for-a-value-serializer"></a>Serviços para um serializador de valor  
 Para o contexto do serializador de valor, você usa um tipo de provedor de <xref:System.Windows.Markup.ValueSerializer> serviço que <xref:System.Windows.Markup.IValueSerializerContext>é específico para a classe,. Esse contexto é passado para substituições dos quatro <xref:System.Windows.Markup.ValueSerializer> métodos virtuais. Chame <xref:System.IServiceProvider.GetService%2A> do contexto para obter serviços.  
  
<a name="using_the_xaml_service_provider_contexts"></a>   
## <a name="using-the-xaml-service-provider-contexts"></a>Usando os contextos do provedor de serviços XAML  
 O provedor de serviços <xref:System.IServiceProvider.GetService%2A> para acesso aos serviços XAML disponíveis para extensões de marcação ou conversores de tipo é implementado como uma classe interna, com exposição somente por meio da interface e como ele é passado para o contexto relevante. Sempre que uma operação de processamento XAML no padrão .NET Framework implementações de serviços XAML do caminho de carga ou do caminho de salvamento invoca a extensão de marcação relevante ou os métodos de conversor de tipo que exigem um contexto de serviço, esse objeto interno é passado. Dependendo da circunstância, o contexto do serviço do sistema fornece um `MarkupExtensionContext` ou `TextSyntaxContext`, mas as especificidades dessas duas classes são internas. Sua interação com essas classes é limitada à solicitação de serviços a partir delas <xref:System.IServiceProvider.GetService%2A>, por meio do.  
  
<a name="available_systemxaml_services"></a>   
## <a name="available-services-from-the-net-framework-xaml-service-context"></a>Serviços disponíveis do .NET Framework contexto do serviço XAML  
 .NET Framework serviços XAML define serviços para extensões de marcação, conversores de tipo, serializadores de valor e potencialmente outros usos. As seções a seguir descrevem cada um desses serviços e fornecem orientação sobre como o serviço pode ser usado em uma implementação.  
  
### <a name="iserviceprovider"></a>IServiceProvider  
 **Documentação de referência**:<xref:System.IServiceProvider>  
  
 **Relevante para:** Operação básica de uma infraestrutura baseada em serviço no .NET Framework para que você possa chamar <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType>.  
  
### <a name="itypedescriptorcontext"></a>ITypeDescriptorContext  
 **Documentação de referência**:<xref:System.ComponentModel.ITypeDescriptorContext>  
  
 Deriva de <xref:System.IServiceProvider>. Essa classe representa o contexto nas assinaturas <xref:System.ComponentModel.TypeConverter> padrão; <xref:System.ComponentModel.TypeConverter> é uma classe que existia desde .NET Framework 1,0. Ele prestringe XAML e o cenário <xref:System.ComponentModel.TypeConverter> XAML para conversão de tipo de valor de cadeia de caracteres. No contexto de serviços XAML .NET Framework, os métodos <xref:System.ComponentModel.TypeConverter> de são implementados explicitamente. O comportamento da implementação explícita indica aos chamadores que a <xref:System.ComponentModel.ITypeDescriptorContext> API não é relevante para sistemas de tipo XAML ou para ler ou gravar objetos do XAML. <xref:System.ComponentModel.ITypeDescriptorContext.Container%2A>, <xref:System.ComponentModel.ITypeDescriptorContext.Instance%2A> `null` e <xref:System.ComponentModel.ITypeDescriptorContext.PropertyDescriptor%2A> geralmente retornam de contextos de serviços XAML .NET Framework.  
  
### <a name="ivalueserializercontext"></a>IValueSerializerContext  
 **Documentação de referência**:<xref:System.Windows.Markup.IValueSerializerContext>  
  
 Deriva de <xref:System.ComponentModel.ITypeDescriptorContext> e também depende de implementações explícitas para suprimir implicações falsas sobre o sistema de tipos XAML. Dá suporte aos métodos auxiliares de <xref:System.Windows.Markup.ValueSerializer>pesquisa estática no.  
  
### <a name="ixamltyperesolver"></a>IXamlTypeResolver  
 **Documentação de referência**:<xref:System.Windows.Markup.IXamlTypeResolver>  
  
 **Definido por:** <xref:System.Windows.Markup> namespace, assembly System. XAML  
  
 **Relevante para:** Cenários de caminho de carga e interação com o contexto de esquema XAML  
  
 **API de serviço:**  <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>  
  
 Pode influenciar o mapeamento de tipo XAML-para-CLR que é necessário quando o gravador XAML constrói um objeto CLR em um grafo de objeto. <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>processa uma cadeia de caracteres potencialmente qualificada por prefixo que corresponde a um nome<xref:System.Xaml.XamlType.Name%2A?displayProperty=nameWithType>de tipo XAML () e <xref:System.Type>retorna um CLR. A resolução de tipos geralmente depende muito do contexto do esquema XAML. Somente o contexto do esquema XAML está ciente de considerações como quais assemblies são carregados e quais desses assemblies podem ou devem ser acessados para a resolução de tipo.  
  
### <a name="iuricontext"></a>IUriContext  
 **Documentação de referência**:<xref:System.Windows.Markup.IUriContext>  
  
 **Definido por:** <xref:System.Windows.Markup> namespace, assembly System. XAML  
  
 **Relevante para:** Carregue o caminho e salve o tratamento de caminho de valores de membro `x:Uri` que são URIs ou valores.  
  
 **API de serviço:**  <xref:System.Windows.Markup.IUriContext.BaseUri%2A>  
  
 Esse serviço relata uma raiz de URI disponível globalmente, se houver. A raiz do URI pode ser usada para resolver URIs relativos para URIs absolutos ou vice-versa. Esse cenário é principalmente relevante para os serviços de aplicativo que são expostos por uma estrutura específica ou recursos de uma classe de elemento raiz usada com frequência em uma estrutura. O URI de base pode ser estabelecido como uma configuração de leitor XAML, que é passada para o gravador de objeto XAML e relatado por esse serviço.  
  
### <a name="iambientprovider"></a>IAmbientProvider  
 **Documentação de referência**:<xref:System.Xaml.IAmbientProvider>  
  
 **Definido por:** <xref:System.Xaml> namespace, assembly System. XAML  
  
 **Relevante para:** Tratamento de caminho de carregamento e desreferenciais de pesquisa de tipo ou otimizações.  
  
 **APIs de serviço:** <xref:System.Xaml.IAmbientProvider.GetAllAmbientValues%2A>, 3 outras.  
  
 O conceito de Ambience em XAML é uma técnica para marcar um membro específico de um tipo como ambiente. Como alternativa, um tipo pode ser ambiente para que todos os valores de propriedade que contenham uma instância do tipo devam ser considerados propriedades de ambiente. As extensões de marcação ou conversores de tipo que estão além do fluxo do nó XAML e que são descendentes no grafo de objeto podem acessar a propriedade de ambiente ou a instância de tipo no tempo de carregamento; ou eles podem usar o conhecimento da estrutura ambiente em tempo de salvamento. Isso pode afetar o grau de qualificação necessário para resolver tipos de outros serviços, como para <xref:System.Windows.Markup.IXamlTypeResolver> o ou para `x:Type`o. Consulte também <xref:System.Xaml.AmbientPropertyValue>.  
  
### <a name="ixamlschemacontextprovider"></a>IXamlSchemaContextProvider  
 **Documentação de referência**:<xref:System.Xaml.IXamlSchemaContextProvider>  
  
 **Definido por:** <xref:System.Xaml> namespace, assembly System. XAML  
  
 **Relevante para:** Caminho de carga e qualquer operação que deva resolver um tipo XAML para um tipo de backup.  
  
 **API de serviço:**  <xref:System.Xaml.IXamlSchemaContextProvider.SchemaContext%2A>  
  
 O contexto de esquema XAML é necessário para qualquer operação de adiamento de carregamento, pois o mesmo contexto de esquema deve agir na área adiada para integrar o conteúdo adiado. Para obter mais informações sobre a função do contexto do esquema XAML, consulte [serviços XAML](index.md).  
  
### <a name="irootobjectprovider"></a>IRootObjectProvider  
 **Documentação de referência**:<xref:System.Xaml.IRootObjectProvider>  
  
 **Definido por:** <xref:System.Xaml> namespace, assembly System. XAML  
  
 **Relevante para:** Caminho de carga.  
  
 **API de serviço:**  <xref:System.Xaml.IRootObjectProvider.RootObject%2A>  
  
 O serviço é relevante para os serviços de aplicativo que são expostos por uma estrutura específica ou por recursos de uma classe de elemento raiz usada com frequência em uma estrutura. Um cenário para obter o objeto raiz é conectar o code-behind e o cabeamento de evento. Por exemplo, a implementação do WPF `x:Class` do é usada para compilação de marcação e fiação de qualquer atributo de manipulador de eventos encontrado em qualquer outra posição na marcação XAML. O ponto de conexão de marcação e classes parciais definidas por code-behind para compilação de marcação está no elemento raiz.  
  
### <a name="ixamlnamespaceresolver"></a>IXamlNamespaceResolver  
 **Documentação de referência**:<xref:System.Xaml.IXamlNamespaceResolver>  
  
 **Definido por:** <xref:System.Xaml> namespace, assembly System. XAML  
  
 **Relevante para:** Caminho de carregamento, salvar caminho.  
  
 **API de serviço:** para caminho de carga <xref:System.Xaml.IXamlNamespaceResolver.GetNamespacePrefixes%2A> , para salvar caminho. <xref:System.Xaml.IXamlNamespaceResolver.GetNamespace%2A>  
  
 <xref:System.Xaml.IXamlNamespaceResolver>é um serviço que pode retornar um identificador/URI de namespace XAML com base em seu prefixo, conforme mapeado na marcação XAML de origem.  
  
### <a name="iprovidevaluetarget"></a>IProvideValueTarget  
 **Documentação de referência**:<xref:System.Windows.Markup.IProvideValueTarget>  
  
 **Definido por:** <xref:System.Windows.Markup> namespace, assembly System. XAML  
  
 **Relevante para:** Carregue o caminho e salve o caminho.  
  
 **APIs de serviço:** <xref:System.Windows.Markup.IProvideValueTarget.TargetObject%2A>, <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A>.  
  
 <xref:System.Windows.Markup.IProvideValueTarget>habilita um conversor de tipo ou extensão de marcação para obter o contexto sobre onde ele está agindo no tempo de carregamento. As implementações podem usar esse contexto para invalidar um uso. Por exemplo, o <xref:System.Windows.DynamicResourceExtension>WPF tem lógica dentro de algumas de suas extensões de marcação, como. A lógica verifica o <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A> para garantir que a extensão seja usada apenas para definir propriedades de dependência (ou uma pequena lista de outras propriedades que não são de dependência).  
  
### <a name="ixamlnameresolver"></a>IXamlNameResolver  
 **Documentação de referência**:<xref:System.Xaml.IXamlNameResolver>  
  
 **Definido por:** <xref:System.Xaml> namespace, assembly System. XAML  
  
 **Relevante para:** Carregue a definição de grafo de objeto de caminho, resolvendo `x:Reference`objetos identificados por `x:Name`, ou técnicas específicas de estrutura.  
  
 **APIs de serviço:** <xref:System.Xaml.IXamlNameResolver.Resolve%2A>; outras APIs para cenários mais avançados, como lidar com referências de encaminhamento.  
  
 A implementação dos serviços XAML .NET Framework `x:Reference` de manipulação depende desse serviço. Estruturas ou ferramentas específicas que dão suporte à estrutura usam esse serviço para `x:Name` tratamento ou manipulação de<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> Propriedade equivalente (atribuída).  
  
### <a name="idestinationtypeprovider"></a>IDestinationTypeProvider  
 **Documentação de referência**:<xref:System.Xaml.IDestinationTypeProvider>  
  
 **Definido por:** <xref:System.Xaml> namespace, assembly System. XAML  
  
 **Relevante para:** Carregar a resolução de caminho de informações indiretas do tipo CLR.  
  
 **API de serviço:** <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>  
  
 Para obter mais informações, consulte <xref:System.Xaml.IDestinationTypeProvider>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [Visão geral das extensões de marcação para XAML](markup-extensions-for-xaml-overview.md)
- [Visão geral de conversores de tipo para XAML](type-converters-for-xaml-overview.md)
