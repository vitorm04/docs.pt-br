---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: 730b1188a95d0e35d7431d43884e867e5520585e
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46568482"
---
# <a name="servicehost"></a><span data-ttu-id="3bcf2-101">\@ServiceHost</span><span class="sxs-lookup"><span data-stu-id="3bcf2-101">\@ServiceHost</span></span>
<span data-ttu-id="3bcf2-102">Associa a fábrica usada para produzir o host de serviço com o serviço hospedado e outros aspectos de programação necessários para acessar ou compilar o código de hospedagem fornecido no arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="3bcf2-102">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bcf2-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3bcf2-103">Syntax</span></span>  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a><span data-ttu-id="3bcf2-104">Atributos</span><span class="sxs-lookup"><span data-stu-id="3bcf2-104">Attributes</span></span>  
  
#### <a name="service"></a><span data-ttu-id="3bcf2-105">Serviço</span><span class="sxs-lookup"><span data-stu-id="3bcf2-105">Service</span></span>  
 <span data-ttu-id="3bcf2-106">O nome do tipo CLR do serviço hospedado.</span><span class="sxs-lookup"><span data-stu-id="3bcf2-106">The CLR type name of the service hosted.</span></span> <span data-ttu-id="3bcf2-107">Isso deve ser um nome qualificado de um tipo que implementa um ou mais dos contatos de serviço.</span><span class="sxs-lookup"><span data-stu-id="3bcf2-107">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>  
  
#### <a name="factory"></a><span data-ttu-id="3bcf2-108">fábrica</span><span class="sxs-lookup"><span data-stu-id="3bcf2-108">Factory</span></span>  
 <span data-ttu-id="3bcf2-109">O nome do tipo CLR da fábrica de host de serviço usado para instanciar o host de serviço.</span><span class="sxs-lookup"><span data-stu-id="3bcf2-109">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="3bcf2-110">Esse atributo é opcional.</span><span class="sxs-lookup"><span data-stu-id="3bcf2-110">This attribute is optional.</span></span> <span data-ttu-id="3bcf2-111">Se não for especificado, o padrão <xref:System.ServiceModel.Activation.ServiceHostFactory> é usado, que retorna uma instância de <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="3bcf2-111">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
#### <a name="debug"></a><span data-ttu-id="3bcf2-112">Depurar</span><span class="sxs-lookup"><span data-stu-id="3bcf2-112">Debug</span></span>  
 <span data-ttu-id="3bcf2-113">Indica se o serviço do Windows Communication Foundation (WCF) deve ser compilado com símbolos de depuração.</span><span class="sxs-lookup"><span data-stu-id="3bcf2-113">Indicates whether the Windows Communication Foundation (WCF) service should be compiled with debug symbols.</span></span> <span data-ttu-id="3bcf2-114">`true` Se o serviço do WCF deve ser compilado com símbolos de depuração; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="3bcf2-114">`true` if the WCF service should be compiled with debug symbols; otherwise, `false`.</span></span>  
  
#### <a name="language"></a><span data-ttu-id="3bcf2-115">Idioma</span><span class="sxs-lookup"><span data-stu-id="3bcf2-115">Language</span></span>  
 <span data-ttu-id="3bcf2-116">Especifica o idioma usado ao compilar todo o código embutido dentro do arquivo (. svc).</span><span class="sxs-lookup"><span data-stu-id="3bcf2-116">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="3bcf2-117">Os valores podem representar qualquer. Linguagens com suporte do NET, incluindo c#, VB e JS, que se referem à linguagem c#, Visual Basic .NET e JScript .NET, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="3bcf2-117">The values can represent any .NET-supported language, including C#, VB, and JS, which refer to C#, Visual Basic .NET, and JScript .NET, respectively.</span></span> <span data-ttu-id="3bcf2-118">Esse atributo é opcional.</span><span class="sxs-lookup"><span data-stu-id="3bcf2-118">This attribute is optional.</span></span>  
  
#### <a name="codebehind"></a><span data-ttu-id="3bcf2-119">Code-behind</span><span class="sxs-lookup"><span data-stu-id="3bcf2-119">CodeBehind</span></span>  
 <span data-ttu-id="3bcf2-120">Especifica o arquivo de origem que implementa o serviço Web XML, quando a classe que implementa o serviço Web XML não reside no mesmo arquivo e não foi compilada em um assembly e colocada no diretório \Bin.</span><span class="sxs-lookup"><span data-stu-id="3bcf2-120">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the \Bin directory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bcf2-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="3bcf2-121">Remarks</span></span>  
 <span data-ttu-id="3bcf2-122">O <xref:System.ServiceModel.ServiceHost> usado para hospedar o serviço é um ponto de extensibilidade dentro do modelo de programação do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3bcf2-122">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the Windows Communication Foundation (WCF) programming model.</span></span> <span data-ttu-id="3bcf2-123">Um padrão de fábrica é usado para instanciar o <xref:System.ServiceModel.ServiceHost> porque ele é, potencialmente, um tipo polimórfico que o ambiente de hospedagem não deve instanciar diretamente.</span><span class="sxs-lookup"><span data-stu-id="3bcf2-123">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>  
  
 <span data-ttu-id="3bcf2-124">A implementação padrão usa <xref:System.ServiceModel.Activation.ServiceHostFactory> para criar uma instância de <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="3bcf2-124">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="3bcf2-125">Mas você pode fornecer sua própria fábrica (um que retorna o seu host derivada), especificando o nome do tipo CLR da sua implementação de fábrica na [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) diretiva.</span><span class="sxs-lookup"><span data-stu-id="3bcf2-125">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive.</span></span>  
  
 <span data-ttu-id="3bcf2-126">Para usar fábrica do host de serviço personalizado próprio em vez do alocador padrão, basta fornecer o nome do tipo de [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) diretiva da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="3bcf2-126">To use you own custom service host factory instead of the default factory, just provide the type name in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive as follows:</span></span>  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="3bcf2-127">Mantenha as implementações de fábrica o mais leves possível.</span><span class="sxs-lookup"><span data-stu-id="3bcf2-127">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="3bcf2-128">Se você tiver muita lógica personalizada, seu código é mais reutilizável se você colocar essa lógica dentro de seu host, em vez de dentro de fábrica.</span><span class="sxs-lookup"><span data-stu-id="3bcf2-128">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>  
  
 <span data-ttu-id="3bcf2-129">Por exemplo, para habilitar um ponto de extremidade habilitados para AJAX `MyService`, especifique o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> para o valor da `Factory` atributo, em vez do padrão <xref:System.ServiceModel.Activation.ServiceHostFactory>, no [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) diretiva como como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3bcf2-129">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3bcf2-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3bcf2-130">Example</span></span>  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3bcf2-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3bcf2-131">See Also</span></span>  
 [<span data-ttu-id="3bcf2-132">Host de serviço personalizado</span><span class="sxs-lookup"><span data-stu-id="3bcf2-132">Custom Service Host</span></span>](../../../../../docs/framework/wcf/samples/custom-service-host.md)
