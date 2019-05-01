---
title: Exemplo de tecnologia de serialização genérica de serviços Web
ms.date: 03/30/2017
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
ms.openlocfilehash: 6549dc1c3d428a5fb74fe0212549ef3f3f6510d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018041"
---
# <a name="web-services-generics-serialization-technology-sample"></a><span data-ttu-id="58e28-102">Exemplo de tecnologia de serialização genérica de serviços Web</span><span class="sxs-lookup"><span data-stu-id="58e28-102">Web Services Generics Serialization Technology Sample</span></span>
[<span data-ttu-id="58e28-103">Baixar Exemplo</span><span class="sxs-lookup"><span data-stu-id="58e28-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 <span data-ttu-id="58e28-104">Esse exemplo mostra como usar e controlar a serialização de genéricos em Serviços Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="58e28-104">This sample shows how to use and control the serialization of generics in ASP.NET Web Services.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="58e28-105">Para criar o exemplo usando Visual Studio</span><span class="sxs-lookup"><span data-stu-id="58e28-105">To build the sample using Visual Studio</span></span>  
  
1. <span data-ttu-id="58e28-106">Abra o Visual Studio e selecione **Novo Site** no menu **Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="58e28-106">Open Visual Studio and select **New Web Site** from the **File** menu.</span></span>  
  
2. <span data-ttu-id="58e28-107">Na caixa de diálogo **Novo Site**, selecione no painel esquerdo a linguagem de programação desejada e, em seguida, no painel esquerdo, selecione **Serviço Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="58e28-107">In the **New Web Site** dialog, select from the left pane your desired programming language, then from the right pane, select **ASP.NET Web Service**.</span></span>  
  
3. <span data-ttu-id="58e28-108">Clique em **Procurar** e navegue para o subdiretório \CS\GenericsService.</span><span class="sxs-lookup"><span data-stu-id="58e28-108">Click **Browse** and navigate to the \CS\GenericsService subdirectory.</span></span>  
  
4. <span data-ttu-id="58e28-109">Selecione Service.asmx para abrir o arquivo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="58e28-109">Select Service.asmx to open the file in Visual Studio.</span></span>  
  
5. <span data-ttu-id="58e28-110">No menu **Compilar**, clique em **Compilar Solução**.</span><span class="sxs-lookup"><span data-stu-id="58e28-110">On the **Build** menu, click **Build Solution**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58e28-111">As primeiras cinco etapas nessa lista são opcionais.</span><span class="sxs-lookup"><span data-stu-id="58e28-111">The first five steps in this list are optional.</span></span> <span data-ttu-id="58e28-112">O tempo de execução do .NET Framework automaticamente gerarão o serviço Web da primeira vez que o serviço for solicitado.</span><span class="sxs-lookup"><span data-stu-id="58e28-112">The .NET Framework runtime will automatically generate the Web service the first time the service is requested.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58e28-113">As seguintes etapas são necessárias para criar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="58e28-113">The following steps are required to build the sample.</span></span>  
  
1. <span data-ttu-id="58e28-114">Abra o [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] e navegue até o subdiretório \CS.</span><span class="sxs-lookup"><span data-stu-id="58e28-114">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to the \CS subdirectory.</span></span>  
  
2. <span data-ttu-id="58e28-115">Clique com o botão direito do mouse no ícone do subdiretório GenericsService e selecione **Compartilhamento e Segurança**.</span><span class="sxs-lookup"><span data-stu-id="58e28-115">Right-click the icon for the GenericsService subdirectory, and select **Sharing and Security**.</span></span>  
  
3. <span data-ttu-id="58e28-116">Na guia **Compartilhamento da Web**, selecione **Compartilhar esta Pasta**.</span><span class="sxs-lookup"><span data-stu-id="58e28-116">In the **Web Sharing** tab, select **Share this Folder**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="58e28-117">Anote o nome do diretório virtual listado no painel **Aliases**, pois você precisará dele para executar a amostra.</span><span class="sxs-lookup"><span data-stu-id="58e28-117">Take note of the virtual directory name that is listed in the **Aliases** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-build-the-sample-using-internet-information-services"></a><span data-ttu-id="58e28-118">Para criar o exemplo usando os Serviços de Informações da Internet</span><span class="sxs-lookup"><span data-stu-id="58e28-118">To build the sample using Internet Information Services</span></span>  
  
1. <span data-ttu-id="58e28-119">Abra o snap-in de gerenciamento **Serviços de Informações da Internet** e expanda **Sites**.</span><span class="sxs-lookup"><span data-stu-id="58e28-119">Open the **Internet Information Services** management snap-in and expand **Web Sites**.</span></span>  
  
2. <span data-ttu-id="58e28-120">Clique com o botão esquerdo do mouse em **Site Padrão**, selecione **Novo** e, em seguida, selecione **Diretório Virtual?** para criar o **Assistente de Criação de Diretório Virtual**.</span><span class="sxs-lookup"><span data-stu-id="58e28-120">Left-click **Default Web Site**, select **New**, and then select **Virtual Directory?** to create the **Virtual Directory Creation Wizard**.</span></span>  
  
3. <span data-ttu-id="58e28-121">Clique em **Avançar**, insira o alias público do diretório virtual e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="58e28-121">Click **Next**, enter the public alias for your virtual directory, and click **Next**.</span></span>  
  
4. <span data-ttu-id="58e28-122">Insira o caminho para o diretório no qual você salvou a amostra (normalmente o subdiretório \CS\GenericsService) e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="58e28-122">Enter the path to the directory where you saved the sample (normally the \CS\GenericsService subdirectory) and click **Next**.</span></span> <span data-ttu-id="58e28-123">Clique em **Avançar** para concluir o assistente.</span><span class="sxs-lookup"><span data-stu-id="58e28-123">Click **Next** to finish the wizard.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="58e28-124">Anote o nome do diretório virtual listado no painel **Alias**, pois você precisará dele para executar a amostra.</span><span class="sxs-lookup"><span data-stu-id="58e28-124">Take note of the virtual directory name that is listed in the **Alias** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="58e28-125">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="58e28-125">To run the sample</span></span>  
  
1. <span data-ttu-id="58e28-126">Abra uma janela do navegador e selecione sua barra de endereços.</span><span class="sxs-lookup"><span data-stu-id="58e28-126">Open a browser window and select its address bar.</span></span>  
  
2. <span data-ttu-id="58e28-127">Tipo de `http://localhost/[virtual directory]/Service.asmx`, onde `[virtual directory]` representa o diretório virtual que você criou ao criar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="58e28-127">Type `http://localhost/[virtual directory]/Service.asmx`, where `[virtual directory]` represents the virtual directory you created when you built the sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58e28-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="58e28-128">Remarks</span></span>  
 <span data-ttu-id="58e28-129">O exemplo exibe uma página ASP.NET padrão que contém links para a definição do Serviço Web.</span><span class="sxs-lookup"><span data-stu-id="58e28-129">The sample displays a default ASP.NET page that contains links to the definition of the Web Service.</span></span> <span data-ttu-id="58e28-130">Você pode personalizar a exibição além de modificar o código de origem para o serviço Web.</span><span class="sxs-lookup"><span data-stu-id="58e28-130">You can customize the display in addition to modifying the source code for the Web service.</span></span> <span data-ttu-id="58e28-131">Para obter mais informações, consulte [Criando clientes de serviço Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w3h45ebk(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="58e28-131">For more information, see [Building XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w3h45ebk(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58e28-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58e28-132">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Web.Services>
- <xref:System.Xml.Serialization>
- [<span data-ttu-id="58e28-133">Serialização</span><span class="sxs-lookup"><span data-stu-id="58e28-133">Serialization</span></span>](../../../docs/standard/serialization/index.md)
- <span data-ttu-id="58e28-134">[Serviços Web XML criados com o ASP.NET e clientes de serviços Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="58e28-134">[XML Web Services Created Using ASP.NET and XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>
