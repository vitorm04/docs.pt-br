---
title: "Como associar a um serviço Web usando o BindingSource dos Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Web services [Windows Forms], binding controls
- BindingSource component [Windows Forms], binding to a Web service
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to Web service
- BindingSource component [Windows Forms], examples
ms.assetid: ee261207-4573-4cb9-a8cb-5185037e0fba
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a647f688f0ae8566a7129982e78e3d9503bee6af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a><span data-ttu-id="c7af7-102">Como associar a um serviço Web usando o BindingSource dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7af7-102">How to: Bind to a Web Service Using the Windows Forms BindingSource</span></span>
<span data-ttu-id="c7af7-103">Se você deseja associar um controle de formulário do Windows para os resultados obtidos de chamar um serviço Web XML, você pode usar um <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="c7af7-103">If you want to bind a Windows Form control to the results obtained from calling an XML Web service, you can use a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="c7af7-104">Esse procedimento é semelhante à associação de um <xref:System.Windows.Forms.BindingSource> um tipo de componente.</span><span class="sxs-lookup"><span data-stu-id="c7af7-104">This procedure is similar to binding a <xref:System.Windows.Forms.BindingSource> component to a type.</span></span> <span data-ttu-id="c7af7-105">É necessário criar um proxy do lado do cliente que contenha os métodos e tipos expostos pelo serviço Web.</span><span class="sxs-lookup"><span data-stu-id="c7af7-105">You must create a client-side proxy that contains the methods and types exposed by the Web service.</span></span> <span data-ttu-id="c7af7-106">O proxy do lado do cliente será gerado pelo próprio serviço Web (.asmx) ou pelo arquivo de linguagem WSDL.</span><span class="sxs-lookup"><span data-stu-id="c7af7-106">You generate a client-side proxy from the Web service (.asmx) itself, or its Web Services Description Language (WSDL) file.</span></span> <span data-ttu-id="c7af7-107">Além disso, o proxy do lado do cliente deve expor os campos dos tipos complexos usados pelo serviço Web como propriedades públicas.</span><span class="sxs-lookup"><span data-stu-id="c7af7-107">Additionally, your client-side proxy must expose the fields of complex types used by the Web service as public properties.</span></span> <span data-ttu-id="c7af7-108">Em seguida, associar a <xref:System.Windows.Forms.BindingSource> para um dos tipos expostos na Web proxy de serviço.</span><span class="sxs-lookup"><span data-stu-id="c7af7-108">You then bind the <xref:System.Windows.Forms.BindingSource> to one of the types exposed in the Web service proxy.</span></span>  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a><span data-ttu-id="c7af7-109">Criar e associar a um proxy do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="c7af7-109">To create and bind to a client-side proxy</span></span>  
  
1.  <span data-ttu-id="c7af7-110">Crie um formulário do Windows Forms em um diretório de sua escolha, com um namespace apropriado.</span><span class="sxs-lookup"><span data-stu-id="c7af7-110">Create a Windows Form in the directory of your choice, with an appropriate namespace.</span></span>  
  
2.  <span data-ttu-id="c7af7-111">Adicionar um <xref:System.Windows.Forms.BindingSource> componente para o formulário.</span><span class="sxs-lookup"><span data-stu-id="c7af7-111">Add a <xref:System.Windows.Forms.BindingSource> component to the form.</span></span>  
  
3.  <span data-ttu-id="c7af7-112">Abra o prompt de comando [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] e acesse o mesmo diretório em que o formulário está localizado.</span><span class="sxs-lookup"><span data-stu-id="c7af7-112">Open the [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] command prompt, and navigate to the same directory that your form is located in.</span></span>  
  
4.  <span data-ttu-id="c7af7-113">Com a ferramenta WSDL, digite `wsdl` e a URL do arquivo .asmx ou WSDL para o serviço Web, seguida pelo namespace do aplicativo e, opcionalmente, o idioma de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c7af7-113">Using the WSDL tool, enter `wsdl` and the URL for the .asmx or WSDL file for the Web service, followed by the namespace of your application, and optionally the language you are working in.</span></span>  
  
     <span data-ttu-id="c7af7-114">O exemplo de código a seguir usa o serviço Web localizado em http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx.</span><span class="sxs-lookup"><span data-stu-id="c7af7-114">The following code example uses the Web service located at http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx.</span></span> <span data-ttu-id="c7af7-115">Por exemplo, para o tipo `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService` do C# ou para o tipo `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB` do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c7af7-115">For example, for C# type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`, or for Visual Basic type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`.</span></span> <span data-ttu-id="c7af7-116">Passar o caminho como um argumento para a ferramenta WSDL gerará um proxy do lado do cliente no mesmo diretório e namespace do aplicativo, no idioma especificado.</span><span class="sxs-lookup"><span data-stu-id="c7af7-116">Passing the path as an argument to the WSDL tool will generate a client-side proxy in the same directory and namespace as your application, in the specified language.</span></span> <span data-ttu-id="c7af7-117">Se [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] estiver sendo usado, adicione o arquivo ao projeto.</span><span class="sxs-lookup"><span data-stu-id="c7af7-117">If you are using [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], add the file to your project.</span></span>  
  
5.  <span data-ttu-id="c7af7-118">Selecione um tipo para associar ao proxy do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="c7af7-118">Select a type in the client-side proxy to bind to.</span></span>  
  
     <span data-ttu-id="c7af7-119">Geralmente, esse é um tipo retornado por um método oferecido pelo serviço Web.</span><span class="sxs-lookup"><span data-stu-id="c7af7-119">This is typically a type returned by a method offered by the Web service.</span></span> <span data-ttu-id="c7af7-120">Os campos do tipo escolhido devem ser expostos como propriedades públicas para fins de associação.</span><span class="sxs-lookup"><span data-stu-id="c7af7-120">The fields of the chosen type must be exposed as public properties for binding purposes.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6.  <span data-ttu-id="c7af7-121">Definir o <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriedade o <xref:System.Windows.Forms.BindingSource> para o tipo que você deseja que é contida no proxy de cliente do serviço Web.</span><span class="sxs-lookup"><span data-stu-id="c7af7-121">Set the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property of the <xref:System.Windows.Forms.BindingSource> to the type you want that is contained in the Web service client-side proxy.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a><span data-ttu-id="c7af7-122">Associar controles ao BindingSource que está associado a um serviço Web</span><span class="sxs-lookup"><span data-stu-id="c7af7-122">To bind controls to the BindingSource that is bound to a Web service</span></span>  
  
-   <span data-ttu-id="c7af7-123">Vincular controles a <xref:System.Windows.Forms.BindingSource>, passando a propriedade pública do tipo de serviço da Web que você deseja como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c7af7-123">Bind controls to the <xref:System.Windows.Forms.BindingSource>, passing the public property of the Web service type that you want as a parameter.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="c7af7-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c7af7-124">Example</span></span>  
 <span data-ttu-id="c7af7-125">O exemplo de código a seguir demonstra como associar um <xref:System.Windows.Forms.BindingSource> componente a um serviço Web e como associar uma caixa de texto para o <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="c7af7-125">The following code example demonstrates how to bind a <xref:System.Windows.Forms.BindingSource> component to a Web service, and then how to bind a text box to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="c7af7-126">Ao clicar no botão, um método de serviço Web será chamado e os resultados serão exibidos no `textbox1`.</span><span class="sxs-lookup"><span data-stu-id="c7af7-126">When you click the button, a Web service method is called and the results will appear in `textbox1`.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c7af7-127">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="c7af7-127">Compiling the Code</span></span>  
 <span data-ttu-id="c7af7-128">Este é um exemplo completo que inclui um método `Main` e uma versão abreviada do código de proxy do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="c7af7-128">This is a complete example that includes a `Main` method, and a shortened version of client-side proxy code.</span></span>  
  
 <span data-ttu-id="c7af7-129">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="c7af7-129">This example requires:</span></span>  
  
-   <span data-ttu-id="c7af7-130">Referências aos assemblies System, System.Drawing, System.Web.Services, System.Windows.Forms e System.Xml.</span><span class="sxs-lookup"><span data-stu-id="c7af7-130">References to the System, System.Drawing, System.Web.Services, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="c7af7-131">Para obter informações sobre como compilar este exemplo na linha de comando para [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consulte [Building from the Command Line (Compilando na linha de comando)](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Compilando pela linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c7af7-131">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="c7af7-132">Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="c7af7-132">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="c7af7-133">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="c7af7-133">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7af7-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7af7-134">See Also</span></span>  
 [<span data-ttu-id="c7af7-135">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="c7af7-135">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="c7af7-136">Como associar um controle do Windows Forms a um tipo</span><span class="sxs-lookup"><span data-stu-id="c7af7-136">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
