---
title: Baixando o Pacote do Manipulador de Token da Web JSON
ms.date: 03/30/2017
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
ms.openlocfilehash: 5a4846a5ec92324105f41b320d0d77f8749c28f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404671"
---
# <a name="downloading-the-json-web-token-handler-package"></a><span data-ttu-id="1e0b9-102">Baixando o Pacote do Manipulador de Token da Web JSON</span><span class="sxs-lookup"><span data-stu-id="1e0b9-102">Downloading the JSON Web Token Handler Package</span></span>
<span data-ttu-id="1e0b9-103">Este tópico descreve como baixar e usar o Manipulador de Token Web JSON no projeto.</span><span class="sxs-lookup"><span data-stu-id="1e0b9-103">This topic discusses how to download and use the JSON Web Token Handler in your project.</span></span>  
  
## <a name="downloading-the-json-web-token-handler"></a><span data-ttu-id="1e0b9-104">Baixando o Manipulador de Token da Web JSON</span><span class="sxs-lookup"><span data-stu-id="1e0b9-104">Downloading the JSON Web Token Handler</span></span>  
 <span data-ttu-id="1e0b9-105">A extensão Manipulador de Token Web JSON está disponível como um pacote NuGet, que adiciona os assemblies e as referências necessárias ao projeto.</span><span class="sxs-lookup"><span data-stu-id="1e0b9-105">The JSON Web Token Handler extension is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="1e0b9-106">Se você ainda não tiver o NuGet instalado, acesse [nuget.org](http://nuget.org) para instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="1e0b9-106">If you do not already have NuGet installed, go to [nuget.org](http://nuget.org) to install it.</span></span> <span data-ttu-id="1e0b9-107">Veja o histórico de controle de versão da extensão visitando sua página no NuGet: [Manipulador de Token Web JSON no NuGet](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span><span class="sxs-lookup"><span data-stu-id="1e0b9-107">You can see the versioning history for the extension by visiting its page on NuGet: [JSON Web Token Handler on NuGet](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span></span>  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-gui"></a><span data-ttu-id="1e0b9-108">Baixando o Manipulador de Token Web JSON usando a GUI do Gerenciador de Pacotes</span><span class="sxs-lookup"><span data-stu-id="1e0b9-108">Downloading the JSON Web Token Handler by using the Package Manager GUI</span></span>  
  
1.  <span data-ttu-id="1e0b9-109">No Visual Studio, clique com o botão direito do mouse no projeto no **Gerenciador de Soluções** e, em seguida, selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="1e0b9-109">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>  
  
2.  <span data-ttu-id="1e0b9-110">Na janela **Gerenciar Pacotes NuGet**, clique na caixa de pesquisa, insira `JWT Token Handler` e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="1e0b9-110">In the **Manage NuGet Packages** window, click the search box and enter `JWT Token Handler` and press **Enter**.</span></span>  
  
3.  <span data-ttu-id="1e0b9-111">No painel de resultados, clique no botão **Instalar** do primeiro resultado.</span><span class="sxs-lookup"><span data-stu-id="1e0b9-111">From the results pane, click the **Install** button for the first result.</span></span>  
  
4.  <span data-ttu-id="1e0b9-112">O download do pacote será iniciado.</span><span class="sxs-lookup"><span data-stu-id="1e0b9-112">The package will begin downloading.</span></span> <span data-ttu-id="1e0b9-113">Antes que ele seja adicionado ao projeto, a caixa de diálogo Aceitação da Licença será exibida.</span><span class="sxs-lookup"><span data-stu-id="1e0b9-113">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="1e0b9-114">Se concordar com os termos de licença, clique em **Eu Aceito**.</span><span class="sxs-lookup"><span data-stu-id="1e0b9-114">If you agree to the license terms, click **I Accept**.</span></span>  
  
5.  <span data-ttu-id="1e0b9-115">Os últimos assemblies do Manipulador de Token Web JSON serão baixados e adicionados ao projeto.</span><span class="sxs-lookup"><span data-stu-id="1e0b9-115">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-console"></a><span data-ttu-id="1e0b9-116">Baixando o Manipulador de Token Web JSON usando o Console do Gerenciador de Pacotes</span><span class="sxs-lookup"><span data-stu-id="1e0b9-116">Downloading the JSON Web Token Handler by using the Package Manager Console</span></span>  
  
1.  <span data-ttu-id="1e0b9-117">No Visual Studio, clique em **Ferramentas**, **Gerenciador de Pacotes da Biblioteca** e, em seguida, em **Console do Gerenciador de Pacotes**.</span><span class="sxs-lookup"><span data-stu-id="1e0b9-117">In Visual Studio, click **Tools**, **Library Package Manager**, and then **Package Manager Console**.</span></span>  
  
2.  <span data-ttu-id="1e0b9-118">O **Console do Gerenciador de Pacotes** será exibido.</span><span class="sxs-lookup"><span data-stu-id="1e0b9-118">The **Package Manager Console** appears.</span></span> <span data-ttu-id="1e0b9-119">Insira o seguinte texto e pressione **Enter**:</span><span class="sxs-lookup"><span data-stu-id="1e0b9-119">Enter the following text and press **Enter**:</span></span>  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.Jwt  
    ```  
  
3.  <span data-ttu-id="1e0b9-120">Os últimos assemblies do Manipulador de Token Web JSON serão baixados e adicionados ao projeto.</span><span class="sxs-lookup"><span data-stu-id="1e0b9-120">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>
