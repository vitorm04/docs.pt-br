---
title: Baixando o Pacote de Registro do nome do emissor de validação
ms.date: 03/30/2017
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
ms.openlocfilehash: 03b68f4b9dc6fde02c951968067e0311e4981d33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398743"
---
# <a name="downloading-the-validating-issuer-name-registry-package"></a><span data-ttu-id="67056-102">Baixando o Pacote de Registro do nome do emissor de validação</span><span class="sxs-lookup"><span data-stu-id="67056-102">Downloading the Validating Issuer Name Registry Package</span></span>
<span data-ttu-id="67056-103">Este tópico descreve como baixar e usar o VINR (Registro do Nome do Emissor de Validação) no projeto.</span><span class="sxs-lookup"><span data-stu-id="67056-103">This topic discusses how to download and use the Validating Issuer Name Registry (VINR) in your project.</span></span>  
  
## <a name="downloading-the-validating-issuer-name-registry"></a><span data-ttu-id="67056-104">Baixando o Registro do Nome do Emissor de Validação</span><span class="sxs-lookup"><span data-stu-id="67056-104">Downloading the Validating Issuer Name Registry</span></span>  
 <span data-ttu-id="67056-105">O VINR está disponível como um pacote NuGet, que adiciona os assemblies e as referências necessárias ao projeto.</span><span class="sxs-lookup"><span data-stu-id="67056-105">The VINR is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="67056-106">Se você ainda não tiver o NuGet instalado, acesse [nuget.org](http://nuget.org) para instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="67056-106">If you do not already have NuGet installed, go to [nuget.org](http://nuget.org) to install it.</span></span> <span data-ttu-id="67056-107">Veja o histórico de controle de versão da extensão visitando sua página no NuGet: [Registro do Nome do Emissor de Validação do Microsoft no NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)</span><span class="sxs-lookup"><span data-stu-id="67056-107">You can see the versioning history for the extension by visiting its page on NuGet: [Microsoft Validating Issuer Name Registry on NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)</span></span>  
  
#### <a name="downloading-the-validating-issuer-name-registry-by-using-the-package-manager-gui"></a><span data-ttu-id="67056-108">Baixando o Registro do Nome do Emissor de Validação usando a GUI do Gerenciador de Pacotes</span><span class="sxs-lookup"><span data-stu-id="67056-108">Downloading the Validating Issuer Name Registry by using the Package Manager GUI</span></span>  
  
1.  <span data-ttu-id="67056-109">No Visual Studio, clique com o botão direito do mouse no projeto no **Gerenciador de Soluções** e, em seguida, selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="67056-109">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>  
  
2.  <span data-ttu-id="67056-110">Na janela **Gerenciar Pacotes NuGet**, clique na caixa de pesquisa, insira `ValidatingIssuerNameRegistry` e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="67056-110">In the **Manage NuGet Packages** window, click the search box and enter `ValidatingIssuerNameRegistry` and press **Enter**.</span></span>  
  
3.  <span data-ttu-id="67056-111">No painel de resultados, clique no botão **Instalar** do primeiro resultado.</span><span class="sxs-lookup"><span data-stu-id="67056-111">From the results pane, click the **Install** button for the first result.</span></span>  
  
4.  <span data-ttu-id="67056-112">O download do pacote será iniciado.</span><span class="sxs-lookup"><span data-stu-id="67056-112">The package will begin downloading.</span></span> <span data-ttu-id="67056-113">Antes que ele seja adicionado ao projeto, a caixa de diálogo Aceitação da Licença será exibida.</span><span class="sxs-lookup"><span data-stu-id="67056-113">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="67056-114">Se concordar com os termos de licença, clique em **Eu Aceito**.</span><span class="sxs-lookup"><span data-stu-id="67056-114">If you agree to the license terms, click **I Accept**.</span></span>  
  
5.  <span data-ttu-id="67056-115">Os últimos assemblies do VINR serão baixados e adicionados ao projeto.</span><span class="sxs-lookup"><span data-stu-id="67056-115">The latest VINR assemblies will be downloaded and added to your project.</span></span>  
  
#### <a name="downloading-the-validating-issuer-name-registry-by-using-the-package-manager-console"></a><span data-ttu-id="67056-116">Baixando o Registro do Nome do Emissor de Validação usando o Console do Gerenciador de Pacotes</span><span class="sxs-lookup"><span data-stu-id="67056-116">Downloading the Validating Issuer Name Registry by using the Package Manager Console</span></span>  
  
1.  <span data-ttu-id="67056-117">No Visual Studio, clique em **Ferramentas**, **Gerenciador de Pacotes da Biblioteca** e, em seguida, em **Console do Gerenciador de Pacotes**.</span><span class="sxs-lookup"><span data-stu-id="67056-117">In Visual Studio, click **Tools**, **Library Package Manager**, and then **Package Manager Console**.</span></span>  
  
2.  <span data-ttu-id="67056-118">O **Console do Gerenciador de Pacotes** será exibido.</span><span class="sxs-lookup"><span data-stu-id="67056-118">The **Package Manager Console** appears.</span></span> <span data-ttu-id="67056-119">Insira o seguinte texto e pressione **Enter**:</span><span class="sxs-lookup"><span data-stu-id="67056-119">Enter the following text and press **Enter**:</span></span>  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry  
    ```  
  
3.  <span data-ttu-id="67056-120">Os últimos assemblies do VINR serão baixados e adicionados ao projeto.</span><span class="sxs-lookup"><span data-stu-id="67056-120">The latest VINR assemblies will be downloaded and added to your project.</span></span>
