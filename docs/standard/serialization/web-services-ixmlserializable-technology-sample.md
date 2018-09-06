---
title: Exemplo de tecnologia IXmlSerializable de serviços Web
ms.date: 03/30/2017
ms.assetid: 0202d3f1-a50b-427d-a5bb-79208b8f1c22
ms.openlocfilehash: 343755c062fc13891d84131a5f7682e2e1466a5a
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43866532"
---
# <a name="web-services-ixmlserializable-technology-sample"></a><span data-ttu-id="6a5cb-102">Exemplo de tecnologia IXmlSerializable de serviços Web</span><span class="sxs-lookup"><span data-stu-id="6a5cb-102">Web Services IXmlSerializable Technology Sample</span></span>
[<span data-ttu-id="6a5cb-103">Baixar Exemplo</span><span class="sxs-lookup"><span data-stu-id="6a5cb-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/IXmlSerializable.zip.exe)  
  
 <span data-ttu-id="6a5cb-104">Esse exemplo mostra como usar o <xref:System.Xml.Serialization.IXmlSerializable> para controlar a serialização de tipos personalizados em Serviços Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6a5cb-104">This sample shows how to use <xref:System.Xml.Serialization.IXmlSerializable> to control the serialization of custom types in ASP.NET Web Services.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="6a5cb-105">Para criar o exemplo usando Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6a5cb-105">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="6a5cb-106">Abra o [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] e selecione **Novo Site** no menu **Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="6a5cb-106">Open [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] and select **New Web Site** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="6a5cb-107">No painel esquerdo da caixa de diálogo **Novo Site**, selecione a linguagem de programação desejada e, em seguida, no painel esquerdo, selecione **Serviço Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="6a5cb-107">In the left pane of the **New Web Site** dialog, select your desired programming language, then from the right pane, select **ASP.NET Web Service**.</span></span>  
  
3.  <span data-ttu-id="6a5cb-108">Digite **IXmlSerializable** como o nome do novo serviço Web.</span><span class="sxs-lookup"><span data-stu-id="6a5cb-108">Type **IXmlSerializable** as the name of the new Web service.</span></span>  
  
4.  <span data-ttu-id="6a5cb-109">Na janela do Gerenciador de Soluções, clique com o botão direito do mouse no ícone de Service.asmx e selecione **Excluir**; repita essa etapa para o arquivo code-behind Service.asmx.</span><span class="sxs-lookup"><span data-stu-id="6a5cb-109">In the Solution Explorer window, right-click the icon for Service.asmx and select **Delete**; repeat this step for the Service.asmx codebehind file.</span></span>  
  
5.  <span data-ttu-id="6a5cb-110">Clique com o botão direito do mouse no diretório do projeto e selecione **Adicionar Item Existente**.</span><span class="sxs-lookup"><span data-stu-id="6a5cb-110">Right-click the project directory and select **Add Existing Item**.</span></span> <span data-ttu-id="6a5cb-111">Na caixa de diálogo, navegue para o subdiretório de Serviço do diretório específico da linguagem.</span><span class="sxs-lookup"><span data-stu-id="6a5cb-111">In the dialog, navigate to the Service subdirectory of the language-specific directory.</span></span>  
  
6.  <span data-ttu-id="6a5cb-112">Selecione Service.asmx e, em seguida, repita essa etapa para o arquivo codebehind Service.asmx.</span><span class="sxs-lookup"><span data-stu-id="6a5cb-112">Select Service.asmx, then repeat this step for the Service.asmx codebehind file.</span></span>  
  
7.  <span data-ttu-id="6a5cb-113">Abra o [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] e navegue para o diretório que contém o diretório IXmlSerializable que você criou na etapa 3 acima.</span><span class="sxs-lookup"><span data-stu-id="6a5cb-113">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to the directory that contains IXmlSerializable directory that you created in step 3 above.</span></span>  
  
8.  <span data-ttu-id="6a5cb-114">Clique com o botão direito do mouse no ícone do diretório IXmlSerializable e selecione **Compartilhamento e Segurança**.</span><span class="sxs-lookup"><span data-stu-id="6a5cb-114">Right-click the icon for the IXmlSerializable directory and select **Sharing and Security**.</span></span>  
  
9. <span data-ttu-id="6a5cb-115">Na guia Compartilhamento da Web, selecione **Compartilhar esta Pasta** e confirme as configurações padrão, incluindo o nome IXmlSerializable.</span><span class="sxs-lookup"><span data-stu-id="6a5cb-115">In the Web Sharing tab, select **Share this Folder**, and confirm the default settings, including the name IXmlSerializable.</span></span>  
  
10. <span data-ttu-id="6a5cb-116">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="6a5cb-116">Click **OK**.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="6a5cb-117">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="6a5cb-117">To run the sample</span></span>  
  
1.  <span data-ttu-id="6a5cb-118">Abra uma janela do navegador e selecione sua barra de endereços.</span><span class="sxs-lookup"><span data-stu-id="6a5cb-118">Open a browser window and select its address bar.</span></span>  
  
2.  <span data-ttu-id="6a5cb-119">Tipo de **http://localhost/IXmlSerializable/Service.asmx**.</span><span class="sxs-lookup"><span data-stu-id="6a5cb-119">Type **http://localhost/IXmlSerializable/Service.asmx**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a5cb-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a5cb-120">See also</span></span>

- <xref:System.Xml.Serialization.IXmlSerializable>  
- <xref:System.Xml.Serialization>  
- <xref:System.Xml.XmlConvert>  
- <xref:System.Xml.XmlQualifiedName>  
- <xref:System.Xml.XmlReader>  
- <xref:System.Xml.Schema.XmlSchema>  
- <xref:System.Xml.Schema.XmlSchemaSet>  
- <xref:System.Xml.XmlUrlResolver>  
- <xref:System.Xml.XmlWriter>
