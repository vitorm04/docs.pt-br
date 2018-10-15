---
title: Baixando o Pacote de Registro do nome do emissor de validação
ms.date: 10/10/2018
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
ms.openlocfilehash: 833a0722fdd27df4e488ed7fac99444c6d9b8905
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2018
ms.locfileid: "49316176"
---
# <a name="download-the-validating-issuer-name-registry-package"></a><span data-ttu-id="0265b-102">Baixe o pacote de registro de nome de emissor validação</span><span class="sxs-lookup"><span data-stu-id="0265b-102">Download the Validating Issuer Name Registry Package</span></span>

<span data-ttu-id="0265b-103">Este tópico descreve como baixar e usar o VINR (Registro do Nome do Emissor de Validação) no projeto.</span><span class="sxs-lookup"><span data-stu-id="0265b-103">This topic discusses how to download and use the Validating Issuer Name Registry (VINR) in your project.</span></span>

<span data-ttu-id="0265b-104">O VINR está disponível como um pacote NuGet, que adiciona os assemblies e as referências necessárias ao projeto.</span><span class="sxs-lookup"><span data-stu-id="0265b-104">The VINR is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="0265b-105">Se você ainda não tiver o NuGet instalado, acesse [nuget.org](https://nuget.org) para instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="0265b-105">If you do not already have NuGet installed, go to [nuget.org](https://nuget.org) to install it.</span></span> <span data-ttu-id="0265b-106">Veja o histórico de controle de versão da extensão visitando sua página no NuGet: [Registro do Nome do Emissor de Validação do Microsoft no NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)</span><span class="sxs-lookup"><span data-stu-id="0265b-106">You can see the versioning history for the extension by visiting its page on NuGet: [Microsoft Validating Issuer Name Registry on NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)</span></span>

## <a name="use-the-package-manager-gui"></a><span data-ttu-id="0265b-107">Usar a GUI do Gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="0265b-107">Use the Package Manager GUI</span></span>

1. <span data-ttu-id="0265b-108">No Visual Studio, clique com o botão direito do mouse no projeto no **Gerenciador de Soluções** e, em seguida, selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="0265b-108">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>

2. <span data-ttu-id="0265b-109">Na janela **Gerenciar Pacotes NuGet**, clique na caixa de pesquisa, insira `ValidatingIssuerNameRegistry` e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="0265b-109">In the **Manage NuGet Packages** window, click the search box and enter `ValidatingIssuerNameRegistry` and press **Enter**.</span></span>

3. <span data-ttu-id="0265b-110">No painel de resultados, clique no botão **Instalar** do primeiro resultado.</span><span class="sxs-lookup"><span data-stu-id="0265b-110">From the results pane, click the **Install** button for the first result.</span></span>

4. <span data-ttu-id="0265b-111">O download do pacote será iniciado.</span><span class="sxs-lookup"><span data-stu-id="0265b-111">The package will begin downloading.</span></span> <span data-ttu-id="0265b-112">Antes que ele seja adicionado ao projeto, a caixa de diálogo Aceitação da Licença será exibida.</span><span class="sxs-lookup"><span data-stu-id="0265b-112">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="0265b-113">Se concordar com os termos de licença, clique em **Eu Aceito**.</span><span class="sxs-lookup"><span data-stu-id="0265b-113">If you agree to the license terms, click **I Accept**.</span></span>

5. <span data-ttu-id="0265b-114">Os últimos assemblies do VINR serão baixados e adicionados ao projeto.</span><span class="sxs-lookup"><span data-stu-id="0265b-114">The latest VINR assemblies will be downloaded and added to your project.</span></span>

## <a name="use-the-package-manager-console"></a><span data-ttu-id="0265b-115">Use o Console do Gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="0265b-115">Use the Package Manager Console</span></span>

1. <span data-ttu-id="0265b-116">No Visual Studio, clique em **ferramentas** > **Gerenciador de pacotes NuGet** > **Package Manager Console**.</span><span class="sxs-lookup"><span data-stu-id="0265b-116">In Visual Studio, click **Tools** > **NuGet Package Manager** > **Package Manager Console**.</span></span>

2. <span data-ttu-id="0265b-117">O **Console do Gerenciador de Pacotes** será exibido.</span><span class="sxs-lookup"><span data-stu-id="0265b-117">The **Package Manager Console** appears.</span></span> <span data-ttu-id="0265b-118">Insira o seguinte texto e pressione **Enter**:</span><span class="sxs-lookup"><span data-stu-id="0265b-118">Enter the following text and press **Enter**:</span></span>

    ```powershell
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry
    ```

3. <span data-ttu-id="0265b-119">Os últimos assemblies do VINR serão baixados e adicionados ao projeto.</span><span class="sxs-lookup"><span data-stu-id="0265b-119">The latest VINR assemblies will be downloaded and added to your project.</span></span>