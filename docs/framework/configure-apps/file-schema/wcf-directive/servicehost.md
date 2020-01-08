---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: 3c7da8d5a473b801da8c48d1cb1504b95cc6c769
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75342127"
---
# <a name="servicehost"></a><span data-ttu-id="04ebc-101">\@ServiceHost</span><span class="sxs-lookup"><span data-stu-id="04ebc-101">\@ServiceHost</span></span>
<span data-ttu-id="04ebc-102">Associa a fábrica usada para produzir o host de serviço com o serviço a ser hospedado e outros aspectos de programação necessários para acessar ou compilar o código de hospedagem fornecido no arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="04ebc-102">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04ebc-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="04ebc-103">Syntax</span></span>  
  
```xml  
<% @ServiceHost
Service = "Service, ServiceNamespace"
Factory = "Factory, FactoryNamespace"
Debug = "Debug"
Language = "Language"
CodeBehind = "CodeBehind"
%>
```  
  
## <a name="attributes"></a><span data-ttu-id="04ebc-104">{1&gt;{2&gt;Atributos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="04ebc-104">Attributes</span></span>  
  
#### <a name="service"></a><span data-ttu-id="04ebc-105">Service</span><span class="sxs-lookup"><span data-stu-id="04ebc-105">Service</span></span>  
 <span data-ttu-id="04ebc-106">O nome do tipo CLR do serviço hospedado.</span><span class="sxs-lookup"><span data-stu-id="04ebc-106">The CLR type name of the service hosted.</span></span> <span data-ttu-id="04ebc-107">Deve ser um nome qualificado de um tipo que implementa um ou mais dos contatos de serviço.</span><span class="sxs-lookup"><span data-stu-id="04ebc-107">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>  
  
#### <a name="factory"></a><span data-ttu-id="04ebc-108">Fábrica</span><span class="sxs-lookup"><span data-stu-id="04ebc-108">Factory</span></span>  
 <span data-ttu-id="04ebc-109">O nome do tipo CLR da fábrica do host de serviço usada para instanciar o host de serviço.</span><span class="sxs-lookup"><span data-stu-id="04ebc-109">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="04ebc-110">Esse atributo é opcional.</span><span class="sxs-lookup"><span data-stu-id="04ebc-110">This attribute is optional.</span></span> <span data-ttu-id="04ebc-111">Se não for especificado, o <xref:System.ServiceModel.Activation.ServiceHostFactory> padrão será usado, que retorna uma instância de <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="04ebc-111">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
#### <a name="debug"></a><span data-ttu-id="04ebc-112">Depuração</span><span class="sxs-lookup"><span data-stu-id="04ebc-112">Debug</span></span>  
 <span data-ttu-id="04ebc-113">Indica se o serviço de Windows Communication Foundation (WCF) deve ser compilado com símbolos de depuração.</span><span class="sxs-lookup"><span data-stu-id="04ebc-113">Indicates whether the Windows Communication Foundation (WCF) service should be compiled with debug symbols.</span></span> <span data-ttu-id="04ebc-114">`true` se o serviço WCF deve ser compilado com símbolos de depuração; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="04ebc-114">`true` if the WCF service should be compiled with debug symbols; otherwise, `false`.</span></span>  
  
#### <a name="language"></a><span data-ttu-id="04ebc-115">{1&gt;Idioma&lt;1}</span><span class="sxs-lookup"><span data-stu-id="04ebc-115">Language</span></span>  
 <span data-ttu-id="04ebc-116">Especifica o idioma usado ao compilar todo o código embutido no arquivo (. svc).</span><span class="sxs-lookup"><span data-stu-id="04ebc-116">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="04ebc-117">Os valores podem representar qualquer. Linguagem com suporte .net, incluindo `C#`, `VB`e `JS`, que se referem C#, Visual Basic e JScript .net, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="04ebc-117">The values can represent any .NET-supported language, including `C#`, `VB`, and `JS`, which refer to C#, Visual Basic, and JScript .NET, respectively.</span></span> <span data-ttu-id="04ebc-118">Esse atributo é opcional.</span><span class="sxs-lookup"><span data-stu-id="04ebc-118">This attribute is optional.</span></span>  
  
#### <a name="codebehind"></a><span data-ttu-id="04ebc-119">CodeBehind</span><span class="sxs-lookup"><span data-stu-id="04ebc-119">CodeBehind</span></span>  
 <span data-ttu-id="04ebc-120">Especifica o arquivo de origem que implementa o serviço Web XML, quando a classe que implementa o serviço Web XML não reside no mesmo arquivo e não foi compilada em um assembly e colocada no diretório \bin.</span><span class="sxs-lookup"><span data-stu-id="04ebc-120">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the \Bin directory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04ebc-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="04ebc-121">Remarks</span></span>  
 <span data-ttu-id="04ebc-122">O <xref:System.ServiceModel.ServiceHost> usado para hospedar o serviço é um ponto de extensibilidade dentro do modelo de programação do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="04ebc-122">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the Windows Communication Foundation (WCF) programming model.</span></span> <span data-ttu-id="04ebc-123">Um padrão de fábrica é usado para instanciar o <xref:System.ServiceModel.ServiceHost> porque ele é, potencialmente, um tipo polimórfico que o ambiente de hospedagem não deve instanciar diretamente.</span><span class="sxs-lookup"><span data-stu-id="04ebc-123">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>  
  
 <span data-ttu-id="04ebc-124">A implementação padrão usa <xref:System.ServiceModel.Activation.ServiceHostFactory> para criar uma instância do <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="04ebc-124">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="04ebc-125">Mas você pode fornecer sua própria fábrica (uma que retorna o host derivado) especificando o nome do tipo CLR de sua implementação de fábrica na diretiva [\@ServiceHost](servicehost.md) .</span><span class="sxs-lookup"><span data-stu-id="04ebc-125">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the [\@ServiceHost](servicehost.md) directive.</span></span>  
  
 <span data-ttu-id="04ebc-126">Para usar sua própria fábrica de hosts de serviço personalizada em vez da fábrica padrão, basta fornecer o nome do tipo na diretiva de [@ServiceHost](servicehost.md) da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="04ebc-126">To use you own custom service host factory instead of the default factory, just provide the type name in the [@ServiceHost](servicehost.md) directive as follows:</span></span>  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="04ebc-127">Mantenha as implementações de fábrica o mais leve possível.</span><span class="sxs-lookup"><span data-stu-id="04ebc-127">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="04ebc-128">Se você tiver muita lógica personalizada, seu código será mais reutilizável se você colocar essa lógica dentro de seu host em vez de dentro da fábrica.</span><span class="sxs-lookup"><span data-stu-id="04ebc-128">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>  
  
 <span data-ttu-id="04ebc-129">Por exemplo, para habilitar um ponto de extremidade habilitado para AJAX para `MyService`, especifique o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> para o valor do atributo `Factory`, em vez do <xref:System.ServiceModel.Activation.ServiceHostFactory>padrão, na diretiva [@ServiceHost](servicehost.md) , conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="04ebc-129">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the [@ServiceHost](servicehost.md) directive as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04ebc-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="04ebc-130">Example</span></span>  
  
```xml  
<% @ServiceHost
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a><span data-ttu-id="04ebc-131">Veja também</span><span class="sxs-lookup"><span data-stu-id="04ebc-131">See also</span></span>

- [<span data-ttu-id="04ebc-132">Host de serviço personalizado</span><span class="sxs-lookup"><span data-stu-id="04ebc-132">Custom Service Host</span></span>](../../../wcf/samples/custom-service-host.md)
