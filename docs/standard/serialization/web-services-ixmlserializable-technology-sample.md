---
title: "Exemplo de tecnologia IXmlSerializable de serviços Web"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0202d3f1-a50b-427d-a5bb-79208b8f1c22
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: be0c76371bda9e91e0becf8a9e09beb44e44dd3c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="web-services-ixmlserializable-technology-sample"></a><span data-ttu-id="59ff1-102">Exemplo de tecnologia IXmlSerializable de serviços Web</span><span class="sxs-lookup"><span data-stu-id="59ff1-102">Web Services IXmlSerializable Technology Sample</span></span>
[<span data-ttu-id="59ff1-103">Baixar Exemplo</span><span class="sxs-lookup"><span data-stu-id="59ff1-103">Download Sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/IXmlSerializable.zip.exe)  
  
 <span data-ttu-id="59ff1-104">Esse exemplo mostra como usar o <xref:System.Xml.Serialization.IXmlSerializable> para controlar a serialização de tipos personalizados em Serviços Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="59ff1-104">This sample shows how to use <xref:System.Xml.Serialization.IXmlSerializable> to control the serialization of custom types in ASP.NET Web Services.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="59ff1-105">Para criar o exemplo usando Visual Studio</span><span class="sxs-lookup"><span data-stu-id="59ff1-105">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="59ff1-106">Abra o [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] e selecione **Novo Site** no menu **Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="59ff1-106">Open [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] and select **New Web Site** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="59ff1-107">No painel esquerdo da caixa de diálogo **Novo Site**, selecione a linguagem de programação desejada e, em seguida, no painel esquerdo, selecione **Serviço Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="59ff1-107">In the left pane of the **New Web Site** dialog, select your desired programming language, then from the right pane, select **ASP.NET Web Service**.</span></span>  
  
3.  <span data-ttu-id="59ff1-108">Digite **IXmlSerializable** como o nome do novo serviço Web.</span><span class="sxs-lookup"><span data-stu-id="59ff1-108">Type **IXmlSerializable** as the name of the new Web service.</span></span>  
  
4.  <span data-ttu-id="59ff1-109">Na janela do Gerenciador de Soluções, clique com o botão direito do mouse no ícone de Service.asmx e selecione **Excluir**; repita essa etapa para o arquivo code-behind Service.asmx.</span><span class="sxs-lookup"><span data-stu-id="59ff1-109">In the Solution Explorer window, right-click the icon for Service.asmx and select **Delete**; repeat this step for the Service.asmx codebehind file.</span></span>  
  
5.  <span data-ttu-id="59ff1-110">Clique com o botão direito do mouse no diretório do projeto e selecione **Adicionar Item Existente**.</span><span class="sxs-lookup"><span data-stu-id="59ff1-110">Right-click the project directory and select **Add Existing Item**.</span></span> <span data-ttu-id="59ff1-111">Na caixa de diálogo, navegue para o subdiretório de Serviço do diretório específico da linguagem.</span><span class="sxs-lookup"><span data-stu-id="59ff1-111">In the dialog, navigate to the Service subdirectory of the language-specific directory.</span></span>  
  
6.  <span data-ttu-id="59ff1-112">Selecione Service.asmx e, em seguida, repita essa etapa para o arquivo codebehind Service.asmx.</span><span class="sxs-lookup"><span data-stu-id="59ff1-112">Select Service.asmx, then repeat this step for the Service.asmx codebehind file.</span></span>  
  
7.  <span data-ttu-id="59ff1-113">Abra o [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] e navegue para o diretório que contém o diretório IXmlSerializable que você criou na etapa 3 acima.</span><span class="sxs-lookup"><span data-stu-id="59ff1-113">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to the directory that contains IXmlSerializable directory that you created in step 3 above.</span></span>  
  
8.  <span data-ttu-id="59ff1-114">Clique com o botão direito do mouse no ícone do diretório IXmlSerializable e selecione **Compartilhamento e Segurança**.</span><span class="sxs-lookup"><span data-stu-id="59ff1-114">Right-click the icon for the IXmlSerializable directory and select **Sharing and Security**.</span></span>  
  
9. <span data-ttu-id="59ff1-115">Na guia Compartilhamento da Web, selecione **Compartilhar esta Pasta** e confirme as configurações padrão, incluindo o nome IXmlSerializable.</span><span class="sxs-lookup"><span data-stu-id="59ff1-115">In the Web Sharing tab, select **Share this Folder**, and confirm the default settings, including the name IXmlSerializable.</span></span>  
  
10. <span data-ttu-id="59ff1-116">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="59ff1-116">Click **OK**.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="59ff1-117">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="59ff1-117">To run the sample</span></span>  
  
1.  <span data-ttu-id="59ff1-118">Abra uma janela do navegador e selecione sua barra de endereços.</span><span class="sxs-lookup"><span data-stu-id="59ff1-118">Open a browser window and select its address bar.</span></span>  
  
2.  <span data-ttu-id="59ff1-119">Digite **http://localhost/IXmlSerializable/Service.asmx**.</span><span class="sxs-lookup"><span data-stu-id="59ff1-119">Type **http://localhost/IXmlSerializable/Service.asmx**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59ff1-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59ff1-120">See Also</span></span>  
 <xref:System.Xml.Serialization.IXmlSerializable>  
 <xref:System.Xml.Serialization>  
 <xref:System.Xml.XmlConvert>  
 <xref:System.Xml.XmlQualifiedName>  
 <xref:System.Xml.XmlReader>  
 <xref:System.Xml.Schema.XmlSchema>  
 <xref:System.Xml.Schema.XmlSchemaSet>  
 <xref:System.Xml.XmlUrlResolver>  
 <xref:System.Xml.XmlWriter>
