---
title: Baixando o Pacote do Manipulador de Token da Web JSON
ms.date: 10/10/2018
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
ms.openlocfilehash: 8f878d23afd76488de7da03f16f72cbfa43c17d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792739"
---
# <a name="download-the-json-web-token-handler-package"></a><span data-ttu-id="3f769-102">Baixe o pacote do manipulador de Token Web JSON</span><span class="sxs-lookup"><span data-stu-id="3f769-102">Download the JSON Web Token Handler Package</span></span>

<span data-ttu-id="3f769-103">Este tópico descreve como baixar e usar o Manipulador de Token Web JSON no projeto.</span><span class="sxs-lookup"><span data-stu-id="3f769-103">This topic discusses how to download and use the JSON Web Token Handler in your project.</span></span>

<span data-ttu-id="3f769-104">A extensão Manipulador de Token Web JSON está disponível como um pacote NuGet, que adiciona os assemblies e as referências necessárias ao projeto.</span><span class="sxs-lookup"><span data-stu-id="3f769-104">The JSON Web Token Handler extension is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="3f769-105">Se você ainda não tiver o NuGet instalado, acesse [nuget.org](https://nuget.org) para instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="3f769-105">If you do not already have NuGet installed, go to [nuget.org](https://nuget.org) to install it.</span></span> <span data-ttu-id="3f769-106">Você pode ver o histórico de controle de versão para a extensão visitando sua página no NuGet: [Manipulador de Token Web JSON no NuGet](https://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span><span class="sxs-lookup"><span data-stu-id="3f769-106">You can see the versioning history for the extension by visiting its page on NuGet: [JSON Web Token Handler on NuGet](https://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span></span>

## <a name="use-the-package-manager-gui"></a><span data-ttu-id="3f769-107">Usar a GUI do Gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="3f769-107">Use the Package Manager GUI</span></span>

1. <span data-ttu-id="3f769-108">No Visual Studio, clique com o botão direito do mouse no projeto no **Gerenciador de Soluções** e, em seguida, selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="3f769-108">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>

2. <span data-ttu-id="3f769-109">Na janela **Gerenciar Pacotes NuGet**, clique na caixa de pesquisa, insira `JWT Token Handler` e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="3f769-109">In the **Manage NuGet Packages** window, click the search box and enter `JWT Token Handler` and press **Enter**.</span></span>

3. <span data-ttu-id="3f769-110">No painel de resultados, clique no botão **Instalar** do primeiro resultado.</span><span class="sxs-lookup"><span data-stu-id="3f769-110">From the results pane, click the **Install** button for the first result.</span></span>

4. <span data-ttu-id="3f769-111">O download do pacote será iniciado.</span><span class="sxs-lookup"><span data-stu-id="3f769-111">The package will begin downloading.</span></span> <span data-ttu-id="3f769-112">Antes que ele seja adicionado ao projeto, a caixa de diálogo Aceitação da Licença será exibida.</span><span class="sxs-lookup"><span data-stu-id="3f769-112">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="3f769-113">Se concordar com os termos de licença, clique em **Eu Aceito**.</span><span class="sxs-lookup"><span data-stu-id="3f769-113">If you agree to the license terms, click **I Accept**.</span></span>

5. <span data-ttu-id="3f769-114">Os últimos assemblies do Manipulador de Token Web JSON serão baixados e adicionados ao projeto.</span><span class="sxs-lookup"><span data-stu-id="3f769-114">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>

## <a name="use-the-package-manager-console"></a><span data-ttu-id="3f769-115">Use o Console do Gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="3f769-115">Use the Package Manager Console</span></span>

1. <span data-ttu-id="3f769-116">No Visual Studio, clique em **ferramentas** > **Gerenciador de pacotes NuGet** > **Package Manager Console**.</span><span class="sxs-lookup"><span data-stu-id="3f769-116">In Visual Studio, click **Tools** > **NuGet Package Manager** > **Package Manager Console**.</span></span>

2. <span data-ttu-id="3f769-117">O **Console do Gerenciador de Pacotes** será exibido.</span><span class="sxs-lookup"><span data-stu-id="3f769-117">The **Package Manager Console** appears.</span></span> <span data-ttu-id="3f769-118">Insira o seguinte texto e pressione **Enter**:</span><span class="sxs-lookup"><span data-stu-id="3f769-118">Enter the following text and press **Enter**:</span></span>

    ```powershell
    Install-Package System.IdentityModel.Tokens.Jwt
    ```

3. <span data-ttu-id="3f769-119">Os últimos assemblies do Manipulador de Token Web JSON serão baixados e adicionados ao projeto.</span><span class="sxs-lookup"><span data-stu-id="3f769-119">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>