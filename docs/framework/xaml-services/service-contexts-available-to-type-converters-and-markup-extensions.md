---
title: Contextos de serviço disponíveis para conversores de tipo e extensões de marcação
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services how-to
ms.assetid: b4dad00f-03da-4579-a4e9-d8d72d2ccbce
ms.openlocfilehash: f3417ed53131a695623ea6c365314ab2c5eedd37
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629287"
---
# <a name="service-contexts-available-to-type-converters-and-markup-extensions"></a>Contextos de serviço disponíveis para conversores de tipo e extensões de marcação
Os autores dos tipos que oferecem suporte a usos de extensão de marcação e de conversor de tipo geralmente devem ter informações contextuais sobre onde um uso está localizado na marcação ou ao redor da estrutura de gráfico de objeto. Informações podem ser necessárias para que o objeto fornecido é instanciado corretamente ou para que as referências de objeto para objetos existentes no grafo de objeto podem ser feitas. Ao usar os serviços de XAML do .NET Framework, o contexto que pode ser necessário é exposto como uma série de interfaces de serviço. Código de suporte de extensão de marcação ou o conversor de tipo pode consultar um serviço usando um contexto de provedor de serviço que está disponível e é passado por meio de <xref:System.Xaml.XamlObjectWriter> ou tipos relacionados. O contexto do esquema XAML está diretamente disponível por meio de um desses serviços. Este tópico descreve como acessar os contextos de serviço de uma implementação de conversor de valor e lista os serviços geralmente disponíveis e suas funções.  
  
<a name="obtaining_services"></a>   
## <a name="obtaining-services"></a>Obtendo serviços  
 Como um implementador de um conversor de valor, você geralmente precisam ter acesso a algum tipo de contexto no qual o conversor de valor é aplicado. Nesse contexto podem incluir informações como o contexto de esquema XAML ativo, acesso ao sistema de mapeamento de tipo que o contexto de esquema XAML e o gravador de XAML do objeto forneçam e assim por diante. Os serviços disponíveis para uma implementação de conversor de tipo ou a extensão de marcação são comunicados por meio dos parâmetros de contexto que fazem parte da assinatura de cada método virtual. Em todos os casos, você tem <xref:System.IServiceProvider> implementado no contexto e pode chamar <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType> para solicitar um serviço.  
  
<a name="services_for_a_markup_extension"></a>   
## <a name="services-for-a-markup-extension"></a>Serviços para uma extensão de marcação  
 <xref:System.Windows.Markup.MarkupExtension> tem apenas um método virtual, <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>. A entrada `serviceProvider` parâmetro é como os serviços são comunicados para implementações de quando a extensão de marcação é chamada por um processador XAML. O pseudocódigo a seguir ilustra como uma implementação de extensão de marcação pode consultar para serviços no seu <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>:  
  
```  
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
 <xref:System.ComponentModel.TypeConverter> tem quatro métodos virtuais que usam um contexto de serviço e que dão suporte a usos XAML. Cada um desses métodos passa uma entrada `context` parâmetro. Esse parâmetro é do tipo <xref:System.ComponentModel.ITypeDescriptorContext>, mas que herda da interface <xref:System.IServiceProvider>e, portanto, há um <xref:System.IServiceProvider.GetService%2A> método disponível para implementações de conversor de tipo.  
  
 O pseudocódigo a seguir ilustra como uma implementação de conversor de tipo para usos XAML pode consultar para serviços em uma das suas substituições, nesse caso, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>:  
  
```  
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
 Para o contexto do serializador de valor, você usar um tipo de provedor de serviço que é específico para o <xref:System.Windows.Markup.ValueSerializer> classe, <xref:System.Windows.Markup.IValueSerializerContext>. Esse contexto é passado para substituições dos quatro <xref:System.Windows.Markup.ValueSerializer> métodos virtuais. Chamar <xref:System.IServiceProvider.GetService%2A> de contexto para obter serviços.  
  
<a name="using_the_xaml_service_provider_contexts"></a>   
## <a name="using-the-xaml-service-provider-contexts"></a>Usando os contextos de provedor de serviço XAML  
 O provedor de serviços para <xref:System.IServiceProvider.GetService%2A> acesso aos serviços XAML disponíveis para conversores de tipo ou de extensões de marcação é implementado como uma classe interna, com exposição apenas por meio da interface e como ele é passado para o contexto relevante. Sempre que uma operação de processamento de XAML em que as implementações padrão de serviços de XAML do .NET Framework de carregar o caminho ou caminho de salvamento invoca os métodos de conversor com marcação relevantes extensão ou tipo que exigem um contexto de serviço, esse objeto interno é passado. Dependendo da circunstância, o contexto de serviço do sistema fornece `MarkupExtensionContext` ou `TextSyntaxContext`, mas as especificidades de ambas essas classes são internas. Sua interação com essas classes é limitada aos serviços solicitantes deles, por meio de <xref:System.IServiceProvider.GetService%2A>.  
  
<a name="available_systemxaml_services"></a>   
## <a name="available-services-from-the-net-framework-xaml-service-context"></a>Serviços disponíveis do que o contexto de serviço XAML do .NET Framework  
 Serviços de XAML do .NET framework define os serviços de extensões de marcação, conversores de tipo, os serializadores de valor e possivelmente outros usos. As seções a seguir descrevem cada um desses serviços e fornecem orientação sobre como o serviço pode ser usado em uma implementação.  
  
### <a name="iserviceprovider"></a>IServiceProvider  
 **Documentação de referência**: <xref:System.IServiceProvider>  
  
 **Relevantes ao:** Operação básica de uma infraestrutura de serviço com base no .NET Framework para que você possa chamar <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType>.  
  
### <a name="itypedescriptorcontext"></a>ITypeDescriptorContext  
 **Documentação de referência**: <xref:System.ComponentModel.ITypeDescriptorContext>  
  
 Deriva de <xref:System.IServiceProvider>. Essa classe representa o contexto no padrão <xref:System.ComponentModel.TypeConverter> assinaturas; <xref:System.ComponentModel.TypeConverter> é uma classe que existe desde o .NET Framework 1.0. Ele antecede o XAML e o XAML <xref:System.ComponentModel.TypeConverter> cenário para conversão de tipo de valor de cadeia de caracteres. O contexto de serviços XAML do .NET Framework, métodos de <xref:System.ComponentModel.TypeConverter> são implementados explicitamente. Comportamento da implementação explícita indica aos chamadores que o <xref:System.ComponentModel.ITypeDescriptorContext> API não é relevante para os sistemas de tipos XAML ou para ler ou gravar objetos do XAML. <xref:System.ComponentModel.ITypeDescriptorContext.Container%2A>, <xref:System.ComponentModel.ITypeDescriptorContext.Instance%2A>, e <xref:System.ComponentModel.ITypeDescriptorContext.PropertyDescriptor%2A> normalmente retornam `null` de contextos de serviços de XAML do .NET Framework.  
  
### <a name="ivalueserializercontext"></a>IValueSerializerContext  
 **Documentação de referência**: <xref:System.Windows.Markup.IValueSerializerContext>  
  
 Deriva de <xref:System.ComponentModel.ITypeDescriptorContext> e também se baseia em implementações explícitas para suprimir falsos implicações sobre o sistema de tipos XAML. Dá suporte a métodos de auxiliares de pesquisa estática em <xref:System.Windows.Markup.ValueSerializer>.  
  
### <a name="ixamltyperesolver"></a>IXamlTypeResolver  
 **Documentação de referência**: <xref:System.Windows.Markup.IXamlTypeResolver>  
  
 **Definido por:** <xref:System.Windows.Markup> namespace, o assembly System. XAML    
  
 **Relevantes ao:** Cenários de caminho de carga e a interação com o contexto de esquema XAML  
  
 **API do serviço:**  <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>  
  
 Pode influenciar o mapeamento de tipo XAML para CLR que é necessário quando o gravador XAML constrói um objeto CLR em um grafo de objeto. <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A> processa uma cadeia de caracteres de prefixo qualificado potencialmente corresponde a um nome de tipo XAML (<xref:System.Xaml.XamlType.Name%2A?displayProperty=nameWithType>) e retorna um CLR <xref:System.Type>. Resolvendo tipos normalmente é muito dependente de contexto do esquema XAML. O contexto de esquema XAML está ciente das considerações, como quais assemblies são carregados e que esses assemblies podem ou devem ser acessados para resolução de tipo.  
  
### <a name="iuricontext"></a>IUriContext  
 **Documentação de referência**: <xref:System.Windows.Markup.IUriContext>  
  
 **Definido por:** <xref:System.Windows.Markup> namespace, o assembly System. XAML    
  
 **Relevantes ao:** Carregar o caminho e salve o tratamento de caminho de valores de membro que são URIs ou `x:Uri` valores.  
  
 **API do serviço:**  <xref:System.Windows.Markup.IUriContext.BaseUri%2A>  
  
 Esse serviço relata uma raiz URI disponível globalmente, se houver. A raiz do URI pode ser usada para resolver URIs relativos para URIs absolutos ou vice-versa. Esse cenário é principalmente relevante para os serviços de aplicativo que são expostos por uma determinada estrutura, ou recursos de uma classe de elemento raiz usados com frequência em uma estrutura. O URI de base pode ser estabelecido como um configuração, de leitor de XAML que, em seguida, é passado para o gravador de objeto XAML e relatado por este serviço.  
  
### <a name="iambientprovider"></a>IAmbientProvider  
 **Documentação de referência**: <xref:System.Xaml.IAmbientProvider>  
  
 **Definido por:** <xref:System.Xaml> namespace, o assembly System. XAML    
  
 **Relevantes ao:** Carregar adiamentos de pesquisa de tratamento e o tipo de caminho ou otimizações.  
  
 **APIs de serviço:**<xref:System.Xaml.IAmbientProvider.GetAllAmbientValues%2A>, 3 outras pessoas.    
  
 O conceito de ambiente no XAML é uma técnica para marcar um membro específico de um tipo como o ambiente. Como alternativa, um tipo pode ser ambiente para que todos os valores de propriedade que mantêm uma instância do tipo devem ser considerados como propriedades de ambiente. Extensões de marcação ou conversores de tipo que estão mais longe o fluxo do nó XAML e que são descendentes no grafo de objeto podem acessar a propriedade de ambiente ou uma instância de tipo em tempo de carregamento; ou eles podem usar o conhecimento da estrutura de ambiente em tempo de salvamento. Isso pode afetar o grau de qualificação que é necessário para resolver tipos para outros serviços, como pelos <xref:System.Windows.Markup.IXamlTypeResolver> ou para `x:Type`. Confira também <xref:System.Xaml.AmbientPropertyValue>.  
  
### <a name="ixamlschemacontextprovider"></a>IXamlSchemaContextProvider  
 **Documentação de referência**: <xref:System.Xaml.IXamlSchemaContextProvider>  
  
 **Definido por:** <xref:System.Xaml> namespace, o assembly System. XAML    
  
 **Relevantes ao:** Caminho de carregamento e qualquer operação que um tipo XAML deve ser resolvido para um tipo de suporte.  
  
 **API do serviço:**  <xref:System.Xaml.IXamlSchemaContextProvider.SchemaContext%2A>  
  
 Contexto de esquema XAML é necessário para operações de carregamento de adiamento, porque o mesmo contexto de esquema deve atuar na área de adiada para integrar o conteúdo adiado. Para obter mais informações sobre a função do contexto de esquema XAML, consulte [serviços de XAML](../../../docs/framework/xaml-services/index.md).  
  
### <a name="irootobjectprovider"></a>IRootObjectProvider  
 **Documentação de referência**: <xref:System.Xaml.IRootObjectProvider>  
  
 **Definido por:** <xref:System.Xaml> namespace, o assembly System. XAML    
  
 **Relevantes ao:** Caminho de carregamento.  
  
 **API do serviço:**  <xref:System.Xaml.IRootObjectProvider.RootObject%2A>  
  
 O serviço é relevante para os serviços de aplicativo que são expostos por uma determinada estrutura ou recursos de uma classe de elemento raiz usados com frequência em uma estrutura. Um cenário para obter o objeto raiz está se conectando a code-behind e fiação de evento. Por exemplo, a implementação de WPF `x:Class` é usado para compilação de marcação e cabeamento de qualquer atributo de manipulador de evento que é encontrado em nenhuma outra posição na marcação XAML. O ponto de conexão de marcação e code-behind definido classes parciais para compilação de marcação é o elemento raiz.  
  
### <a name="ixamlnamespaceresolver"></a>IXamlNamespaceResolver  
 **Documentação de referência**: <xref:System.Xaml.IXamlNamespaceResolver>  
  
 **Definido por:** <xref:System.Xaml> namespace, o assembly System. XAML    
  
 **Relevantes ao:** Caminho de carregamento, caminho de salvamento.  
  
 **API do serviço:** <xref:System.Xaml.IXamlNamespaceResolver.GetNamespace%2A> para o caminho de carga, <xref:System.Xaml.IXamlNamespaceResolver.GetNamespacePrefixes%2A> para caminho de salvamento.  
  
 <xref:System.Xaml.IXamlNamespaceResolver> é um serviço que pode retornar um identificador de namespace XAML / URI com base em seu prefixo conforme mapeado na marcação XAML da origem.  
  
### <a name="iprovidevaluetarget"></a>IProvideValueTarget  
 **Documentação de referência**: <xref:System.Windows.Markup.IProvideValueTarget>  
  
 **Definido por:** <xref:System.Windows.Markup> namespace, o assembly System. XAML    
  
 **Relevantes ao:** Carregar o caminho e salve o caminho.  
  
 **APIs de serviço:**<xref:System.Windows.Markup.IProvideValueTarget.TargetObject%2A>, <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A>.    
  
 <xref:System.Windows.Markup.IProvideValueTarget> permite que uma extensão de marcação ou o conversor de tipo obter o contexto sobre onde ele está atuando em tempo de carregamento. Implementações podem usar este contexto para invalidar um uso. Por exemplo, o WPF tem lógica dentro de algumas de suas extensões de marcação, como <xref:System.Windows.DynamicResourceExtension>. As verificações de lógica de <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A> para certificar-se de que a extensão só é usada para definir as propriedades de dependência (ou uma lista curta de outras propriedades não são de dependência).  
  
### <a name="ixamlnameresolver"></a>IXamlNameResolver  
 **Documentação de referência**: <xref:System.Xaml.IXamlNameResolver>  
  
 **Definido por:** <xref:System.Xaml> namespace, o assembly System. XAML    
  
 **Relevantes ao:** Carregar a definição de grafo de objeto de caminho, resolvendo os objetos identificados por `x:Name`, `x:Reference`, ou técnicas específicas do framework.  
  
 **APIs de serviço:**<xref:System.Xaml.IXamlNameResolver.Resolve%2A>; outras APIs para cenários mais avançados, como lidar com referências de encaminhamento.    
  
 A implementação de serviços de XAML do .NET Framework de `x:Reference` tratamento depende desse serviço. Estruturas específicas ou ferramentas que dão suporte a estrutura de usam esse serviço para `x:Name` manipulação ou equivalente (<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> atribuído) tratamento de propriedade.  
  
### <a name="idestinationtypeprovider"></a>IDestinationTypeProvider  
 **Documentação de referência**: <xref:System.Xaml.IDestinationTypeProvider>  
  
 **Definido por:** <xref:System.Xaml> namespace, o assembly System. XAML    
  
 **Relevantes ao:** Resolução de caminho indiretas CLR de informações de tipo de carga.  
  
 **API do serviço:** <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>  
  
 Para obter mais informações, consulte <xref:System.Xaml.IDestinationTypeProvider>.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [Visão geral das extensões de marcação para XAML](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)
- [Visão geral de conversores de tipo para XAML](../../../docs/framework/xaml-services/type-converters-for-xaml-overview.md)
