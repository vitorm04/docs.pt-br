---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: cb425d9f4dadd97e93946a2b4cd9d059ea8504ce
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051357"
---
# <a name="servicehost"></a><span data-ttu-id="71c49-101">\@ServiceHost</span><span class="sxs-lookup"><span data-stu-id="71c49-101">\@ServiceHost</span></span>

<span data-ttu-id="71c49-102">Associa a fábrica usada para produzir o host de serviço com o serviço a ser hospedado e outros aspectos de programação necessários para acessar ou compilar o código de hospedagem fornecido no arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="71c49-102">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>

## <a name="syntax"></a><span data-ttu-id="71c49-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="71c49-103">Syntax</span></span>

```aspx-csharp
<% @ServiceHost
Service = "Service, ServiceNamespace"
Factory = "Factory, FactoryNamespace"
Debug = "Debug"
Language = "Language"
CodeBehind = "CodeBehind"
%>
```

## <a name="attributes"></a><span data-ttu-id="71c49-104">Atributos</span><span class="sxs-lookup"><span data-stu-id="71c49-104">Attributes</span></span>

### <a name="service"></a><span data-ttu-id="71c49-105">Serviço</span><span class="sxs-lookup"><span data-stu-id="71c49-105">Service</span></span>

<span data-ttu-id="71c49-106">O nome do tipo CLR do serviço hospedado.</span><span class="sxs-lookup"><span data-stu-id="71c49-106">The CLR type name of the service hosted.</span></span> <span data-ttu-id="71c49-107">Deve ser um nome qualificado de um tipo que implementa um ou mais dos contatos de serviço.</span><span class="sxs-lookup"><span data-stu-id="71c49-107">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>

### <a name="factory"></a><span data-ttu-id="71c49-108">Factory</span><span class="sxs-lookup"><span data-stu-id="71c49-108">Factory</span></span>

<span data-ttu-id="71c49-109">O nome do tipo CLR da fábrica do host de serviço usada para instanciar o host de serviço.</span><span class="sxs-lookup"><span data-stu-id="71c49-109">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="71c49-110">Esse atributo é opcional.</span><span class="sxs-lookup"><span data-stu-id="71c49-110">This attribute is optional.</span></span> <span data-ttu-id="71c49-111">Se não for especificado, o padrão <xref:System.ServiceModel.Activation.ServiceHostFactory> será usado, que retorna uma instância de <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="71c49-111">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>

### <a name="debug"></a><span data-ttu-id="71c49-112">Depurar</span><span class="sxs-lookup"><span data-stu-id="71c49-112">Debug</span></span>

<span data-ttu-id="71c49-113">Indica se o serviço de Windows Communication Foundation (WCF) deve ser compilado com símbolos de depuração.</span><span class="sxs-lookup"><span data-stu-id="71c49-113">Indicates whether the Windows Communication Foundation (WCF) service should be compiled with debug symbols.</span></span> <span data-ttu-id="71c49-114">`true`Se o serviço WCF deve ser compilado com símbolos de depuração; caso contrário, `false` .</span><span class="sxs-lookup"><span data-stu-id="71c49-114">`true` if the WCF service should be compiled with debug symbols; otherwise, `false`.</span></span>

### <a name="language"></a><span data-ttu-id="71c49-115">Linguagem</span><span class="sxs-lookup"><span data-stu-id="71c49-115">Language</span></span>

<span data-ttu-id="71c49-116">Especifica o idioma usado ao compilar todo o código embutido no arquivo (. svc).</span><span class="sxs-lookup"><span data-stu-id="71c49-116">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="71c49-117">Os valores podem representar qualquer. Linguagem com suporte .net, incluindo `C#` , `VB` e `JS` , que se refere a C#, Visual Basic e JScript .net, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="71c49-117">The values can represent any .NET-supported language, including `C#`, `VB`, and `JS`, which refer to C#, Visual Basic, and JScript .NET, respectively.</span></span> <span data-ttu-id="71c49-118">Esse atributo é opcional.</span><span class="sxs-lookup"><span data-stu-id="71c49-118">This attribute is optional.</span></span>

### <a name="codebehind"></a><span data-ttu-id="71c49-119">CodeBehind</span><span class="sxs-lookup"><span data-stu-id="71c49-119">CodeBehind</span></span>

<span data-ttu-id="71c49-120">Especifica o arquivo de origem que implementa o serviço Web XML, quando a classe que implementa o serviço Web XML não reside no mesmo arquivo e não foi compilada em um assembly e colocada no diretório *\Bin* .</span><span class="sxs-lookup"><span data-stu-id="71c49-120">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the *\Bin* directory.</span></span>

## <a name="remarks"></a><span data-ttu-id="71c49-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="71c49-121">Remarks</span></span>

<span data-ttu-id="71c49-122">O <xref:System.ServiceModel.ServiceHost> usado para hospedar o serviço é um ponto de extensibilidade dentro do modelo de programação de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="71c49-122">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the Windows Communication Foundation (WCF) programming model.</span></span> <span data-ttu-id="71c49-123">Um padrão de fábrica é usado para instanciar o <xref:System.ServiceModel.ServiceHost> porque é, potencialmente, um tipo polimórfico que o ambiente de hospedagem não deve instanciar diretamente.</span><span class="sxs-lookup"><span data-stu-id="71c49-123">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>

<span data-ttu-id="71c49-124">A implementação padrão usa o <xref:System.ServiceModel.Activation.ServiceHostFactory> para criar uma instância do <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="71c49-124">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="71c49-125">Mas você pode fornecer sua própria fábrica (uma que retorna o host derivado) especificando o nome do tipo CLR da sua implementação de fábrica na `@ServiceHost` diretiva.</span><span class="sxs-lookup"><span data-stu-id="71c49-125">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the `@ServiceHost` directive.</span></span>

<span data-ttu-id="71c49-126">Para usar sua própria fábrica de hosts de serviço personalizada em vez da fábrica padrão, basta fornecer o nome do tipo na `@ServiceHost` diretiva da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="71c49-126">To use you own custom service host factory instead of the default factory, just provide the type name in the `@ServiceHost` directive as follows.</span></span>

```xml
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>
```

<span data-ttu-id="71c49-127">Mantenha as implementações de fábrica o mais leve possível.</span><span class="sxs-lookup"><span data-stu-id="71c49-127">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="71c49-128">Se você tiver muita lógica personalizada, seu código será mais reutilizável se você colocar essa lógica dentro de seu host em vez de dentro da fábrica.</span><span class="sxs-lookup"><span data-stu-id="71c49-128">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>

<span data-ttu-id="71c49-129">Por exemplo, para habilitar um ponto de extremidade habilitado para AJAX para `MyService` , especifique o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> para o valor do `Factory` atributo, em vez do padrão <xref:System.ServiceModel.Activation.ServiceHostFactory> , na `@ServiceHost` diretiva, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="71c49-129">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the `@ServiceHost` directive as shown in the following example:</span></span>

```aspx-csharp
<% @ServiceHost
Service="MyService"
Language="C#"
Debug="true"
Factory="WebScriptServiceHostFactory"
%>
```

## <a name="see-also"></a><span data-ttu-id="71c49-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71c49-130">See also</span></span>

- [<span data-ttu-id="71c49-131">Host de serviço personalizado</span><span class="sxs-lookup"><span data-stu-id="71c49-131">Custom Service Host</span></span>](../../../wcf/samples/custom-service-host.md)
