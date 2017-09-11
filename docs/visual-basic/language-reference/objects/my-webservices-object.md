---
title: Objeto My. WebServices | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
dev_langs:
- VB
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: eff9296c4b3ba0714737b63f977dbeec30c54c9a
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="mywebservices-object"></a><span data-ttu-id="4b899-102">Objeto My.WebServices</span><span class="sxs-lookup"><span data-stu-id="4b899-102">My.WebServices Object</span></span>
<span data-ttu-id="4b899-103">Fornece propriedades para criar e acessar uma única instância de cada serviço Web XML referenciado pelo projeto atual.</span><span class="sxs-lookup"><span data-stu-id="4b899-103">Provides properties for creating and accessing a single instance of each XML Web service referenced by the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b899-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="4b899-104">Remarks</span></span>  
 <span data-ttu-id="4b899-105">O `My.WebServices` objeto fornece uma instância de cada serviço Web referenciado pelo projeto atual.</span><span class="sxs-lookup"><span data-stu-id="4b899-105">The `My.WebServices` object provides an instance of each Web service referenced by the current project.</span></span> <span data-ttu-id="4b899-106">Cada instância é instanciada por demanda.</span><span class="sxs-lookup"><span data-stu-id="4b899-106">Each instance is instantiated on demand.</span></span> <span data-ttu-id="4b899-107">Você pode acessar esses serviços da Web através das propriedades do `My.WebServices` objeto.</span><span class="sxs-lookup"><span data-stu-id="4b899-107">You can access these Web services through the properties of the `My.WebServices` object.</span></span> <span data-ttu-id="4b899-108">O nome da propriedade é igual ao nome do serviço Web que acessa a propriedade.</span><span class="sxs-lookup"><span data-stu-id="4b899-108">The name of the property is the same as the name of the Web service that the property accesses.</span></span> <span data-ttu-id="4b899-109">Qualquer classe que herda de <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>é um serviço Web.</xref:System.Web.Services.Protocols.SoapHttpClientProtocol></span><span class="sxs-lookup"><span data-stu-id="4b899-109">Any class that inherits from <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> is a Web service.</span></span> <span data-ttu-id="4b899-110">Para obter informações sobre como adicionar os serviços da Web a um projeto, consulte [acessar o aplicativo Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).</span><span class="sxs-lookup"><span data-stu-id="4b899-110">For information about adding Web services to a project, see [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="4b899-111">O `My.WebServices` objeto expõe apenas os serviços Web associados ao projeto atual.</span><span class="sxs-lookup"><span data-stu-id="4b899-111">The `My.WebServices` object exposes only the Web services associated with the current project.</span></span> <span data-ttu-id="4b899-112">Ele não fornece acesso aos Web services declarados em DLLs referenciados.</span><span class="sxs-lookup"><span data-stu-id="4b899-112">It does not provide access to Web services declared in referenced DLLs.</span></span> <span data-ttu-id="4b899-113">Para acessar um serviço Web que fornece uma DLL, você deve usar o nome qualificado do serviço da Web, no formulário *DllName*.* WebServiceName*.</span><span class="sxs-lookup"><span data-stu-id="4b899-113">To access a Web service that a DLL provides, you must use the qualified name of the Web service, in the form *DllName*.*WebServiceName*.</span></span> <span data-ttu-id="4b899-114">Para obter mais informações, consulte [acessar o aplicativo Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).</span><span class="sxs-lookup"><span data-stu-id="4b899-114">For more information, see [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="4b899-115">O objeto e suas propriedades não estão disponíveis para aplicativos da Web.</span><span class="sxs-lookup"><span data-stu-id="4b899-115">The object and its properties are not available for Web applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4b899-116">Propriedades</span><span class="sxs-lookup"><span data-stu-id="4b899-116">Properties</span></span>  
 <span data-ttu-id="4b899-117">Cada propriedade do `My.WebServices` objeto fornece acesso a uma instância de um serviço Web referenciado pelo projeto atual.</span><span class="sxs-lookup"><span data-stu-id="4b899-117">Each property of the `My.WebServices` object provides access to an instance of a Web service referenced by the current project.</span></span> <span data-ttu-id="4b899-118">O nome da propriedade é igual ao nome do serviço Web que acessa a propriedade e o tipo de propriedade é o mesmo tipo do serviço Web.</span><span class="sxs-lookup"><span data-stu-id="4b899-118">The name of the property is the same as the name of the Web service that the property accesses, and the property type is the same as the Web service's type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b899-119">Se houver uma colisão de nomes, o nome da propriedade para acessar um serviço da Web é *RootNamespace*_*Namespace*\_*ServiceName*.</span><span class="sxs-lookup"><span data-stu-id="4b899-119">If there is a name collision, the property name for accessing a Web service is *RootNamespace*_*Namespace*\_*ServiceName*.</span></span> <span data-ttu-id="4b899-120">Por exemplo, considere dois serviços Web chamados `Service1`.</span><span class="sxs-lookup"><span data-stu-id="4b899-120">For example, consider two Web services named `Service1`.</span></span> <span data-ttu-id="4b899-121">Se um desses serviços é o namespace raiz `WindowsApplication1` e no namespace `Namespace1`, você poderia acessar esse serviço usando `My.WebServices.WindowsApplication1_Namespace1_Service1`.</span><span class="sxs-lookup"><span data-stu-id="4b899-121">If one of these services is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that service by using `My.WebServices.WindowsApplication1_Namespace1_Service1`.</span></span>  
  
 <span data-ttu-id="4b899-122">Quando você acessa pela primeira vez um do `My.WebServices` propriedades do objeto, ele cria uma nova instância do serviço da Web e o armazena.</span><span class="sxs-lookup"><span data-stu-id="4b899-122">When you first access one of the `My.WebServices` object's properties, it creates a new instance of the Web service and stores it.</span></span> <span data-ttu-id="4b899-123">Os acessos subsequentes dessa propriedade retornam essa instância do serviço da Web.</span><span class="sxs-lookup"><span data-stu-id="4b899-123">Subsequent accesses of that property return that instance of the Web service.</span></span>  
  
 <span data-ttu-id="4b899-124">Você pode descartar um serviço da Web atribuindo `Nothing` para a propriedade para o serviço da Web.</span><span class="sxs-lookup"><span data-stu-id="4b899-124">You can dispose of a Web service by assigning `Nothing` to the property for that Web service.</span></span> <span data-ttu-id="4b899-125">Atribui o setter da propriedade `Nothing` para o valor armazenado.</span><span class="sxs-lookup"><span data-stu-id="4b899-125">The property setter assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="4b899-126">Se você atribuir qualquer valor diferente de `Nothing` à propriedade setter lança um <xref:System.ArgumentException>exceção.</xref:System.ArgumentException></span><span class="sxs-lookup"><span data-stu-id="4b899-126">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="4b899-127">Você pode testar se uma propriedade do `My.WebServices` objeto armazena uma instância do serviço da Web usando o `Is` ou `IsNot` operador.</span><span class="sxs-lookup"><span data-stu-id="4b899-127">You can test whether a property of the `My.WebServices` object stores an instance of the Web service by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="4b899-128">Você pode usar os operadores para verificar se o valor da propriedade é `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="4b899-128">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b899-129">Normalmente, o `Is` ou `IsNot` operador precisa ler o valor da propriedade para executar a comparação.</span><span class="sxs-lookup"><span data-stu-id="4b899-129">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="4b899-130">No entanto, se a propriedade armazena atualmente `Nothing`, a propriedade cria uma nova instância do serviço da Web e, em seguida, retorna essa instância.</span><span class="sxs-lookup"><span data-stu-id="4b899-130">However, if the property currently stores `Nothing`, the property creates a new instance of the Web service and then returns that instance.</span></span> <span data-ttu-id="4b899-131">No entanto, o compilador Visual Basic trata as propriedades do `My.WebServices` especialmente de objeto e permite que o `Is` ou `IsNot` operador para verificar o status da propriedade sem alterar seu valor.</span><span class="sxs-lookup"><span data-stu-id="4b899-131">However, the Visual Basic compiler treats the properties of the `My.WebServices` object specially, and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b899-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4b899-132">Example</span></span>  
 <span data-ttu-id="4b899-133">Este exemplo chama o `FahrenheitToCelsius` método o `TemperatureConverter` XML Web Services e retorna o resultado.</span><span class="sxs-lookup"><span data-stu-id="4b899-133">This example calls the `FahrenheitToCelsius` method of the `TemperatureConverter` XML Web service, and returns the result.</span></span>  
  
 <span data-ttu-id="4b899-134">[!code-vb[VbVbalrMyWebService n º&1;](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-webservices-object_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4b899-134">[!code-vb[VbVbalrMyWebService#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-webservices-object_1.vb)]</span></span>  
  
 <span data-ttu-id="4b899-135">Para esse exemplo funcione, seu projeto deve fazer referência a um serviço Web denominado `Converter`, e o serviço Web deve expor o `ConvertTemperature` método.</span><span class="sxs-lookup"><span data-stu-id="4b899-135">For this example to work, your project must reference a Web service named `Converter`, and that Web service must expose the `ConvertTemperature` method.</span></span> <span data-ttu-id="4b899-136">Para obter mais informações, consulte [acessar o aplicativo Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).</span><span class="sxs-lookup"><span data-stu-id="4b899-136">For more information, see [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="4b899-137">Esse código não funciona em um projeto de aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="4b899-137">This code does not work in a Web application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b899-138">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4b899-138">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="4b899-139">Disponibilidade por tipo de projeto</span><span class="sxs-lookup"><span data-stu-id="4b899-139">Availability by Project Type</span></span>  
  
|<span data-ttu-id="4b899-140">Tipo de projeto</span><span class="sxs-lookup"><span data-stu-id="4b899-140">Project type</span></span>|<span data-ttu-id="4b899-141">Disponível</span><span class="sxs-lookup"><span data-stu-id="4b899-141">Available</span></span>|  
|---|---|  
|<span data-ttu-id="4b899-142">Aplicativo do Windows</span><span class="sxs-lookup"><span data-stu-id="4b899-142">Windows Application</span></span>|<span data-ttu-id="4b899-143">**Sim**</span><span class="sxs-lookup"><span data-stu-id="4b899-143">**Yes**</span></span>|  
|<span data-ttu-id="4b899-144">Biblioteca de Classes</span><span class="sxs-lookup"><span data-stu-id="4b899-144">Class Library</span></span>|<span data-ttu-id="4b899-145">**Sim**</span><span class="sxs-lookup"><span data-stu-id="4b899-145">**Yes**</span></span>|  
|<span data-ttu-id="4b899-146">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="4b899-146">Console Application</span></span>|<span data-ttu-id="4b899-147">**Sim**</span><span class="sxs-lookup"><span data-stu-id="4b899-147">**Yes**</span></span>|  
|<span data-ttu-id="4b899-148">Biblioteca de controle do Windows</span><span class="sxs-lookup"><span data-stu-id="4b899-148">Windows Control Library</span></span>|<span data-ttu-id="4b899-149">**Sim**</span><span class="sxs-lookup"><span data-stu-id="4b899-149">**Yes**</span></span>|  
|<span data-ttu-id="4b899-150">Biblioteca de Controles da Web</span><span class="sxs-lookup"><span data-stu-id="4b899-150">Web Control Library</span></span>|<span data-ttu-id="4b899-151">**Sim**</span><span class="sxs-lookup"><span data-stu-id="4b899-151">**Yes**</span></span>|  
|<span data-ttu-id="4b899-152">Serviço do Windows</span><span class="sxs-lookup"><span data-stu-id="4b899-152">Windows Service</span></span>|<span data-ttu-id="4b899-153">**Sim**</span><span class="sxs-lookup"><span data-stu-id="4b899-153">**Yes**</span></span>|  
|<span data-ttu-id="4b899-154">Site</span><span class="sxs-lookup"><span data-stu-id="4b899-154">Web Site</span></span>|<span data-ttu-id="4b899-155">Não</span><span class="sxs-lookup"><span data-stu-id="4b899-155">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4b899-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b899-156">See Also</span></span>  
 <span data-ttu-id="4b899-157"><xref:System.Web.Services.Protocols.SoapHttpClientProtocol></xref:System.Web.Services.Protocols.SoapHttpClientProtocol></span><span class="sxs-lookup"><span data-stu-id="4b899-157"><xref:System.Web.Services.Protocols.SoapHttpClientProtocol></span></span>   
 <span data-ttu-id="4b899-158"><xref:System.ArgumentException></xref:System.ArgumentException></span><span class="sxs-lookup"><span data-stu-id="4b899-158"><xref:System.ArgumentException></span></span>   
<span data-ttu-id="4b899-159"> [Acessando serviços Web do aplicativo](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)</span><span class="sxs-lookup"><span data-stu-id="4b899-159"> [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)</span></span>
