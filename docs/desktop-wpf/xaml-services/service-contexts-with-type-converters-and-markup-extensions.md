---
title: Contextos de serviço disponíveis para conversores de tipo e extensões de marcação
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services how-to
ms.assetid: b4dad00f-03da-4579-a4e9-d8d72d2ccbce
ms.openlocfilehash: 59c4385eb4df8c622be6164cdb0a1a911c445ca8
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071657"
---
# <a name="service-contexts-available-to-type-converters-and-markup-extensions"></a>Contextos de serviço disponíveis para conversores de tipo e extensões de marcação
Os autores dos tipos que suportam os usos de conversor de tipo e extensão de marcação devem muitas vezes ter informações contextuais sobre onde um uso está localizado na marcação ou na estrutura do gráfico de objetos ao redor. Informações podem ser necessárias para que o objeto fornecido seja instanciado corretamente ou para que as referências de objetos aos objetos existentes no gráfico do objeto possam ser feitas. Ao usar o .NET XAML Services, o contexto que pode ser necessário é exposto como uma série de interfaces de serviço. O código de suporte de extensão de tipo conversor ou de extensão <xref:System.Xaml.XamlObjectWriter> de marcação pode consultar um serviço usando um contexto de provedor de serviços disponível e passado de tipos ou relacionados. O contexto do esquema XAML está disponível diretamente através de um desses serviços. Este tópico descreve como acessar contextos de serviço a partir de uma implementação de conversor de valor e lista serviços tipicamente disponíveis e suas funções.

## <a name="obtaining-services"></a>Obtenção de serviços

Como um implementador de um conversor de valor, muitas vezes você precisa acessar algum tipo de contexto no qual o conversor de valor é aplicado. Esse contexto pode incluir informações como o contexto ativo do esquema XAML, acesso ao sistema de mapeamento de tipo que o contexto do esquema XAML e o escritor de objetos XAML fornecem, e assim por diante. Os serviços disponíveis para uma extensão de marcação ou implementação do conversor de tipo são comunicados através dos parâmetros de contexto que fazem parte da assinatura de cada método virtual. Em todos os <xref:System.IServiceProvider> casos, você implementou <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType> no contexto, e pode ligar para solicitar um serviço.

## <a name="services-for-a-markup-extension"></a>Serviços para uma extensão de marcação

<xref:System.Windows.Markup.MarkupExtension>tem apenas um <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>método virtual, . O `serviceProvider` parâmetro de entrada é como os serviços são comunicados às implementações quando a extensão de marcação é chamada por um processador XAML. O pseudocódigo a seguir ilustra como uma implementação de <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>extensão de marcação pode consultar serviços em seu :

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

## <a name="services-for-a-type-converter"></a>Serviços para um conversor de tipo

<xref:System.ComponentModel.TypeConverter>tem quatro métodos virtuais que usam um contexto de serviço e que suportam os usos de XAML. Cada um desses métodos `context` passa um parâmetro de entrada. Este parâmetro é <xref:System.ComponentModel.ITypeDescriptorContext>de tipo, mas <xref:System.IServiceProvider>essa interface herda <xref:System.IServiceProvider.GetService%2A> , e, portanto, há um método disponível para digitar implementações de conversor.

O pseudocódigo a seguir ilustra como uma implementação de conversor de tipo para usos <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>XAML pode consultar serviços em uma de suas substituições, neste caso :

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

## <a name="services-for-a-value-serializer"></a>Serviços para um Serializador de valor

Para o contexto serializador de valor, você <xref:System.Windows.Markup.ValueSerializer> usa <xref:System.Windows.Markup.IValueSerializerContext>um tipo de provedor de serviços específico para a classe, . Esse contexto é passado para <xref:System.Windows.Markup.ValueSerializer> as substituições dos quatro métodos virtuais. Ligue <xref:System.IServiceProvider.GetService%2A> do contexto para obter serviços.

## <a name="using-the-xaml-service-provider-contexts"></a>Usando os contextos do provedor de serviços XAML

O provedor <xref:System.IServiceProvider.GetService%2A> de serviços para acesso aos serviços XAML disponíveis para marcação de extensões ou conversores de tipo é implementado como uma classe interna, com exposição apenas através da interface e como ela é passada para o contexto relevante. Sempre que uma operação de processamento XAML na implementação padrão do .NET XAML Services do caminho de carga ou do caminho de salvamento invoca os métodos relevantes de extensão de marcação ou tipo conversor que requerem um contexto de serviço, este objeto interno é passado. Dependendo da circunstância, o contexto `MarkupExtensionContext` de `TextSyntaxContext`serviço do sistema fornece ou , mas as especificidades de ambas as classes são internas. Sua interação com essas classes limita-se a <xref:System.IServiceProvider.GetService%2A>solicitar serviços deles, através de .

## <a name="available-services-from-the-net-xaml-service-context"></a>Serviços disponíveis do .NET XAML Service Context

.NET Os serviços XAML definem serviços para extensões de marcação, conversores de tipo, serializadores de valor e, potencialmente, outros usos. As seções a seguir descrevem cada um desses serviços e fornecem orientações sobre como o serviço pode ser usado em uma implementação.

### <a name="iserviceprovider"></a>IServiceProvider

**Documentação de referência**:<xref:System.IServiceProvider>

**Relevante para:** Operação básica de uma infra-estrutura baseada em serviços em .NET para que você possa ligar <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType>.

### <a name="itypedescriptorcontext"></a>Itypedescriptorcontext

**Documentação de referência**:<xref:System.ComponentModel.ITypeDescriptorContext>

Deriva de <xref:System.IServiceProvider>. Esta classe representa contexto <xref:System.ComponentModel.TypeConverter> nas assinaturas padrão; <xref:System.ComponentModel.TypeConverter> é uma classe que existe desde .NET Framework 1.0. Ele antecede o XAML <xref:System.ComponentModel.TypeConverter> e o cenário XAML para conversão do tipo string-value. No contexto .NET XAML Services, os métodos <xref:System.ComponentModel.TypeConverter> são implementados explicitamente. O comportamento da implementação explícita indica <xref:System.ComponentModel.ITypeDescriptorContext> aos chamadores que a API não é relevante para sistemas do tipo XAML ou para ler ou escrever objetos de XAML. <xref:System.ComponentModel.ITypeDescriptorContext.Container%2A>, <xref:System.ComponentModel.ITypeDescriptorContext.Instance%2A>e <xref:System.ComponentModel.ITypeDescriptorContext.PropertyDescriptor%2A> geralmente `null` retornam dos contextos de Serviços XAML .NET.

### <a name="ivalueserializercontext"></a>Ivalueserializercontext

**Documentação de referência**:<xref:System.Windows.Markup.IValueSerializerContext>

Deriva <xref:System.ComponentModel.ITypeDescriptorContext> e também conta com implementações explícitas para suprimir falsas implicações sobre o sistema do tipo XAML. Suporta os métodos de ajuda <xref:System.Windows.Markup.ValueSerializer>de procurar estática saciados .

### <a name="ixamltyperesolver"></a>Ixamltyperesolver

**Documentação de referência**:<xref:System.Windows.Markup.IXamlTypeResolver>

**Definido por:** <xref:System.Windows.Markup> namespace, System.Xaml assembly  

**Relevante para:** Cenários de caminho de carga e interação com o contexto do esquema XAML

**API de serviço:**  <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>

Pode influenciar o mapeamento do tipo XAML-para-CLR que é necessário quando o escritor XAML constrói um objeto CLR em um gráfico de objetos. <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>processa uma seqüência potencialmente qualificada por prefixo<xref:System.Xaml.XamlType.Name%2A?displayProperty=nameWithType>que corresponde a <xref:System.Type>um nome do tipo XAML ( ), e retorna uma CLR . A resolução de tipos é tipicamente fortemente dependente do contexto do esquema XAML. Apenas o contexto do esquema XAML está ciente de considerações como quais conjuntos são carregados e quais desses conjuntos podem ou devem ser acessados para resolução de tipos.

### <a name="iuricontext"></a>Iuricontext

**Documentação de referência**:<xref:System.Windows.Markup.IUriContext>

**Definido por:** <xref:System.Windows.Markup> namespace, System.Xaml assembly  

**Relevante para:** Carregar caminho e salvar o manuseio do caminho `x:Uri` dos valores de membro que são URIs ou valores.

**API de serviço:**  <xref:System.Windows.Markup.IUriContext.BaseUri%2A>

Este serviço relata uma raiz URI disponível globalmente, se houver. A raiz URI pode ser usada para resolver URIs relativos para URIs absolutas ou vice-versa. Esse cenário é principalmente relevante para serviços de aplicativos que são expostos por uma determinada estrutura, ou recursos de uma classe de elementoraiz frequentemente usada em uma estrutura. O URI base pode ser estabelecido como uma configuração de leitor XAML, que é então passada para o escritor de objetos XAML e relatada por este serviço.

### <a name="iambientprovider"></a>Iambientprovider

**Documentação de referência**:<xref:System.Xaml.IAmbientProvider>

**Definido por:** <xref:System.Xaml> namespace, System.Xaml assembly  

**Relevante para:** Manuseio do caminho de carga e desmensagens de visualização de tipo.

**APIs de serviço:**  <xref:System.Xaml.IAmbientProvider.GetAllAmbientValues%2A>, três outras.

O conceito de ambiência em XAML é uma técnica para marcar um determinado membro de um tipo como ambiente. Alternativamente, um tipo pode ser ambiente para que todos os valores de propriedade que possuem uma instância do tipo devem ser considerados propriedades ambientais. As extensões de marcação ou conversores de tipo que estão mais ao longo do fluxo de nós XAML e que são descendentes no gráfico de objetos podem acessar a propriedade ambiente ou a instância de tipo no momento da carga; ou eles podem usar o conhecimento da estrutura ambiente em tempo útil. Isso pode afetar o grau de qualificação necessário para resolver <xref:System.Windows.Markup.IXamlTypeResolver> tipos `x:Type`de outros serviços, como para ou para . Consulte também <xref:System.Xaml.AmbientPropertyValue>.

### <a name="ixamlschemacontextprovider"></a>Ixamlschemacontextprovider

**Documentação de referência**:<xref:System.Xaml.IXamlSchemaContextProvider>

**Definido por:** <xref:System.Xaml> namespace, System.Xaml assembly  

**Relevante para:** Caminho de carga e qualquer operação que deva resolver um tipo XAML para um tipo de backup.

**API de serviço:**  <xref:System.Xaml.IXamlSchemaContextProvider.SchemaContext%2A>

O contexto do esquema XAML é necessário para qualquer operação de carga de adiamento, pois o mesmo contexto de esquema deve agir na área diferida para integrar o conteúdo diferido. Para obter mais informações sobre o papel do contexto do esquema XAML, consulte [XAML Services](../../../api/index.md).

### <a name="irootobjectprovider"></a>Irootobjectprovider

**Documentação de referência**:<xref:System.Xaml.IRootObjectProvider>

**Definido por:** <xref:System.Xaml> namespace, System.Xaml assembly  

**Relevante para:** Caminho de carga.

**API de serviço:**  <xref:System.Xaml.IRootObjectProvider.RootObject%2A>

O serviço é relevante para serviços de aplicativos que são expostos por uma estrutura específica ou por recursos de uma classe de elementoraiz frequentemente usada em uma estrutura. Um cenário para obter o objeto raiz é conectar o código atrás e a fiação do evento. Por exemplo, a implementação do `x:Class` WPF é usada para compilar e fiação de qualquer atributo de manipulador de eventos que seja encontrado em qualquer outra posição na marcação XAML. O ponto de conexão de marcação e código atrás de classes parciais definidas para compilação de marcação está no elemento raiz.

### <a name="ixamlnamespaceresolver"></a>IXamlNamespaceResolver

**Documentação de referência**:<xref:System.Xaml.IXamlNamespaceResolver>

**Definido por:** <xref:System.Xaml> namespace, System.Xaml assembly  

**Relevante para:** Caminho de carga, salve o caminho.

**API de serviço:** <xref:System.Xaml.IXamlNamespaceResolver.GetNamespace%2A> <xref:System.Xaml.IXamlNamespaceResolver.GetNamespacePrefixes%2A> para caminho de carga, para salvar caminho.

<xref:System.Xaml.IXamlNamespaceResolver>é um serviço que pode retornar um identificador de namespace XAML / URI com base em seu prefixo como mapeado na marcação XAML de origem.

### <a name="iprovidevaluetarget"></a>Iprovidevaluetarget

**Documentação de referência**:<xref:System.Windows.Markup.IProvideValueTarget>

**Definido por:** <xref:System.Windows.Markup> namespace, System.Xaml assembly  

**Relevante para:** Carregar o caminho e salvar o caminho.

**APIs de serviço:**<xref:System.Windows.Markup.IProvideValueTarget.TargetObject%2A>, <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A>.  

<xref:System.Windows.Markup.IProvideValueTarget>permite que um conversor de tipo ou extensão de marcação obtenha contexto sobre onde ele está agindo no tempo de carga. Implementações podem usar esse contexto para invalidar um uso. Por exemplo, o WPF tem lógica dentro de <xref:System.Windows.DynamicResourceExtension>algumas de suas extensões de marcação, tais como . A lógica <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A> verifica se a extensão é usada apenas para definir propriedades de dependência (ou uma pequena lista de outras propriedades não-dependência).

### <a name="ixamlnameresolver"></a>Ixamlnameresolver

**Documentação de referência**:<xref:System.Xaml.IXamlNameResolver>

**Definido por:** <xref:System.Xaml> namespace, System.Xaml assembly  

**Relevante para:** Definição do gráfico do objeto de `x:Name` `x:Reference`caminho de carga, resolvendo objetos identificados por , ou técnicas específicas de estrutura.

**APIs de serviço:**  <xref:System.Xaml.IXamlNameResolver.Resolve%2A>; outras APIs para cenários mais avançados, como lidar com referências avançadas.

A implementação de `x:Reference` serviços .NET XAML depende desse serviço. Estruturas ou ferramentas específicas que suportam `x:Name` a estrutura usam<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> este serviço para manuseio ou tratamento de propriedade equivalente (atribuído).

### <a name="idestinationtypeprovider"></a>Provedor de iDestinoType

**Documentação de referência**:<xref:System.Xaml.IDestinationTypeProvider>

**Definido por:** <xref:System.Xaml> namespace, System.Xaml assembly  

**Relevante para:** Resolução do caminho de carga de informações do tipo CLR indiretas.

**API de serviço:**<xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>

Para obter mais informações, consulte <xref:System.Xaml.IDestinationTypeProvider>.

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [Visão geral das extensões de marcação para XAML](markup-extensions-overview.md)
- [Visão geral de conversores de tipo para XAML](type-converters-overview.md)
