---
title: 'Como: Associar a um serviço Web usando o BindingSource do Windows Forms'
ms.date: 03/30/2017
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
ms.openlocfilehash: a8fb10fef8e4b5624d8066a15d12d6efd1e62dee
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590508"
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a><span data-ttu-id="ef021-102">Como: Associar a um serviço Web usando o BindingSource do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ef021-102">How to: Bind to a Web Service Using the Windows Forms BindingSource</span></span>
<span data-ttu-id="ef021-103">Se você quiser associar um controle de formulário do Windows aos resultados obtidos chamando um serviço Web XML, você pode usar um <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="ef021-103">If you want to bind a Windows Form control to the results obtained from calling an XML Web service, you can use a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="ef021-104">Esse procedimento é semelhante à associação de um <xref:System.Windows.Forms.BindingSource> um tipo de componente.</span><span class="sxs-lookup"><span data-stu-id="ef021-104">This procedure is similar to binding a <xref:System.Windows.Forms.BindingSource> component to a type.</span></span> <span data-ttu-id="ef021-105">É necessário criar um proxy do lado do cliente que contenha os métodos e tipos expostos pelo serviço Web.</span><span class="sxs-lookup"><span data-stu-id="ef021-105">You must create a client-side proxy that contains the methods and types exposed by the Web service.</span></span> <span data-ttu-id="ef021-106">O proxy do lado do cliente será gerado pelo próprio serviço Web (.asmx) ou pelo arquivo de linguagem WSDL.</span><span class="sxs-lookup"><span data-stu-id="ef021-106">You generate a client-side proxy from the Web service (.asmx) itself, or its Web Services Description Language (WSDL) file.</span></span> <span data-ttu-id="ef021-107">Além disso, o proxy do lado do cliente deve expor os campos dos tipos complexos usados pelo serviço Web como propriedades públicas.</span><span class="sxs-lookup"><span data-stu-id="ef021-107">Additionally, your client-side proxy must expose the fields of complex types used by the Web service as public properties.</span></span> <span data-ttu-id="ef021-108">Em seguida, você associa o <xref:System.Windows.Forms.BindingSource> para um dos tipos expostos na Web do proxy de serviço.</span><span class="sxs-lookup"><span data-stu-id="ef021-108">You then bind the <xref:System.Windows.Forms.BindingSource> to one of the types exposed in the Web service proxy.</span></span>  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a><span data-ttu-id="ef021-109">Criar e associar a um proxy do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="ef021-109">To create and bind to a client-side proxy</span></span>  
  
1. <span data-ttu-id="ef021-110">Crie um formulário do Windows Forms em um diretório de sua escolha, com um namespace apropriado.</span><span class="sxs-lookup"><span data-stu-id="ef021-110">Create a Windows Form in the directory of your choice, with an appropriate namespace.</span></span>  
  
2. <span data-ttu-id="ef021-111">Adicionar um <xref:System.Windows.Forms.BindingSource> componente para o formulário.</span><span class="sxs-lookup"><span data-stu-id="ef021-111">Add a <xref:System.Windows.Forms.BindingSource> component to the form.</span></span>  
  
3. <span data-ttu-id="ef021-112">Abra o prompt de comando [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] e acesse o mesmo diretório em que o formulário está localizado.</span><span class="sxs-lookup"><span data-stu-id="ef021-112">Open the [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] command prompt, and navigate to the same directory that your form is located in.</span></span>  
  
4. <span data-ttu-id="ef021-113">Com a ferramenta WSDL, digite `wsdl` e a URL do arquivo .asmx ou WSDL para o serviço Web, seguida pelo namespace do aplicativo e, opcionalmente, o idioma de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ef021-113">Using the WSDL tool, enter `wsdl` and the URL for the .asmx or WSDL file for the Web service, followed by the namespace of your application, and optionally the language you are working in.</span></span>  
  
     <span data-ttu-id="ef021-114">O exemplo de código a seguir usa o serviço Web localizado em `http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx`.</span><span class="sxs-lookup"><span data-stu-id="ef021-114">The following code example uses the Web service located at `http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx`.</span></span> <span data-ttu-id="ef021-115">Por exemplo, para o tipo `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService` do C# ou para o tipo `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB` do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ef021-115">For example, for C# type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`, or for Visual Basic type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`.</span></span> <span data-ttu-id="ef021-116">Passar o caminho como um argumento para a ferramenta WSDL gerará um proxy do lado do cliente no mesmo diretório e namespace do aplicativo, no idioma especificado.</span><span class="sxs-lookup"><span data-stu-id="ef021-116">Passing the path as an argument to the WSDL tool will generate a client-side proxy in the same directory and namespace as your application, in the specified language.</span></span> <span data-ttu-id="ef021-117">Se você estiver usando o Visual Studio, adicione o arquivo ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="ef021-117">If you are using Visual Studio, add the file to your project.</span></span>  
  
5. <span data-ttu-id="ef021-118">Selecione um tipo para associar ao proxy do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="ef021-118">Select a type in the client-side proxy to bind to.</span></span>  
  
     <span data-ttu-id="ef021-119">Geralmente, esse é um tipo retornado por um método oferecido pelo serviço Web.</span><span class="sxs-lookup"><span data-stu-id="ef021-119">This is typically a type returned by a method offered by the Web service.</span></span> <span data-ttu-id="ef021-120">Os campos do tipo escolhido devem ser expostos como propriedades públicas para fins de associação.</span><span class="sxs-lookup"><span data-stu-id="ef021-120">The fields of the chosen type must be exposed as public properties for binding purposes.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6. <span data-ttu-id="ef021-121">Defina as <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriedade do <xref:System.Windows.Forms.BindingSource> para o tipo desejado, que é contido no proxy do lado do cliente de serviço Web.</span><span class="sxs-lookup"><span data-stu-id="ef021-121">Set the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property of the <xref:System.Windows.Forms.BindingSource> to the type you want that is contained in the Web service client-side proxy.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a><span data-ttu-id="ef021-122">Associar controles ao BindingSource que está associado a um serviço Web</span><span class="sxs-lookup"><span data-stu-id="ef021-122">To bind controls to the BindingSource that is bound to a Web service</span></span>  
  
- <span data-ttu-id="ef021-123">Vincular controles a <xref:System.Windows.Forms.BindingSource>, passando a propriedade pública do tipo de serviço da Web que você deseja como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ef021-123">Bind controls to the <xref:System.Windows.Forms.BindingSource>, passing the public property of the Web service type that you want as a parameter.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="ef021-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ef021-124">Example</span></span>  
 <span data-ttu-id="ef021-125">O exemplo de código a seguir demonstra como associar um <xref:System.Windows.Forms.BindingSource> componente a um serviço Web e, em seguida, como associar uma caixa de texto para o <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="ef021-125">The following code example demonstrates how to bind a <xref:System.Windows.Forms.BindingSource> component to a Web service, and then how to bind a text box to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="ef021-126">Ao clicar no botão, um método de serviço Web será chamado e os resultados serão exibidos no `textbox1`.</span><span class="sxs-lookup"><span data-stu-id="ef021-126">When you click the button, a Web service method is called and the results will appear in `textbox1`.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ef021-127">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="ef021-127">Compiling the Code</span></span>  
 <span data-ttu-id="ef021-128">Este é um exemplo completo que inclui um método `Main` e uma versão abreviada do código de proxy do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="ef021-128">This is a complete example that includes a `Main` method, and a shortened version of client-side proxy code.</span></span>  
  
 <span data-ttu-id="ef021-129">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="ef021-129">This example requires:</span></span>  
  
- <span data-ttu-id="ef021-130">Referências aos assemblies System, System.Drawing, System.Web.Services, System.Windows.Forms e System.Xml.</span><span class="sxs-lookup"><span data-stu-id="ef021-130">References to the System, System.Drawing, System.Web.Services, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef021-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef021-131">See also</span></span>

- [<span data-ttu-id="ef021-132">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="ef021-132">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="ef021-133">Como: Associar um controle dos Windows Forms a um tipo</span><span class="sxs-lookup"><span data-stu-id="ef021-133">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
