---
title: Baixando o Pacote do Manipulador de Token da Web JSON
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: d3821ff1da945df7c6e07e5baf69730173eacc87
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="downloading-the-json-web-token-handler-package"></a><span data-ttu-id="b151d-102">Baixando o Pacote do Manipulador de Token da Web JSON</span><span class="sxs-lookup"><span data-stu-id="b151d-102">Downloading the JSON Web Token Handler Package</span></span>
<span data-ttu-id="b151d-103">Este tópico descreve como baixar e usar o Manipulador de Token Web JSON no projeto.</span><span class="sxs-lookup"><span data-stu-id="b151d-103">This topic discusses how to download and use the JSON Web Token Handler in your project.</span></span>  
  
## <a name="downloading-the-json-web-token-handler"></a><span data-ttu-id="b151d-104">Baixando o Manipulador de Token da Web JSON</span><span class="sxs-lookup"><span data-stu-id="b151d-104">Downloading the JSON Web Token Handler</span></span>  
 <span data-ttu-id="b151d-105">A extensão Manipulador de Token Web JSON está disponível como um pacote NuGet, que adiciona os assemblies e as referências necessárias ao projeto.</span><span class="sxs-lookup"><span data-stu-id="b151d-105">The JSON Web Token Handler extension is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="b151d-106">Se você ainda não tiver o NuGet instalado, acesse [nuget.org](http://nuget.org) para instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="b151d-106">If you do not already have NuGet installed, go to [nuget.org](http://nuget.org) to install it.</span></span> <span data-ttu-id="b151d-107">Veja o histórico de controle de versão da extensão visitando sua página no NuGet: [Manipulador de Token Web JSON no NuGet](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span><span class="sxs-lookup"><span data-stu-id="b151d-107">You can see the versioning history for the extension by visiting its page on NuGet: [JSON Web Token Handler on NuGet](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span></span>  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-gui"></a><span data-ttu-id="b151d-108">Baixando o Manipulador de Token Web JSON usando a GUI do Gerenciador de Pacotes</span><span class="sxs-lookup"><span data-stu-id="b151d-108">Downloading the JSON Web Token Handler by using the Package Manager GUI</span></span>  
  
1.  <span data-ttu-id="b151d-109">No Visual Studio, clique com o botão direito do mouse no projeto no **Gerenciador de Soluções** e, em seguida, selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="b151d-109">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>  
  
2.  <span data-ttu-id="b151d-110">Na janela **Gerenciar Pacotes NuGet**, clique na caixa de pesquisa, insira `JWT Token Handler` e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="b151d-110">In the **Manage NuGet Packages** window, click the search box and enter `JWT Token Handler` and press **Enter**.</span></span>  
  
3.  <span data-ttu-id="b151d-111">No painel de resultados, clique no botão **Instalar** do primeiro resultado.</span><span class="sxs-lookup"><span data-stu-id="b151d-111">From the results pane, click the **Install** button for the first result.</span></span>  
  
4.  <span data-ttu-id="b151d-112">O download do pacote será iniciado.</span><span class="sxs-lookup"><span data-stu-id="b151d-112">The package will begin downloading.</span></span> <span data-ttu-id="b151d-113">Antes que ele seja adicionado ao projeto, a caixa de diálogo Aceitação da Licença será exibida.</span><span class="sxs-lookup"><span data-stu-id="b151d-113">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="b151d-114">Se concordar com os termos de licença, clique em **Eu Aceito**.</span><span class="sxs-lookup"><span data-stu-id="b151d-114">If you agree to the license terms, click **I Accept**.</span></span>  
  
5.  <span data-ttu-id="b151d-115">Os últimos assemblies do Manipulador de Token Web JSON serão baixados e adicionados ao projeto.</span><span class="sxs-lookup"><span data-stu-id="b151d-115">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-console"></a><span data-ttu-id="b151d-116">Baixando o Manipulador de Token Web JSON usando o Console do Gerenciador de Pacotes</span><span class="sxs-lookup"><span data-stu-id="b151d-116">Downloading the JSON Web Token Handler by using the Package Manager Console</span></span>  
  
1.  <span data-ttu-id="b151d-117">No Visual Studio, clique em **Ferramentas**, **Gerenciador de Pacotes da Biblioteca** e, em seguida, em **Console do Gerenciador de Pacotes**.</span><span class="sxs-lookup"><span data-stu-id="b151d-117">In Visual Studio, click **Tools**, **Library Package Manager**, and then **Package Manager Console**.</span></span>  
  
2.  <span data-ttu-id="b151d-118">O **Console do Gerenciador de Pacotes** será exibido.</span><span class="sxs-lookup"><span data-stu-id="b151d-118">The **Package Manager Console** appears.</span></span> <span data-ttu-id="b151d-119">Insira o seguinte texto e pressione **Enter**:</span><span class="sxs-lookup"><span data-stu-id="b151d-119">Enter the following text and press **Enter**:</span></span>  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.Jwt  
    ```  
  
3.  <span data-ttu-id="b151d-120">Os últimos assemblies do Manipulador de Token Web JSON serão baixados e adicionados ao projeto.</span><span class="sxs-lookup"><span data-stu-id="b151d-120">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>
