---
title: Configurando os Serviços de informação da internet 7.0 para o Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 13fd068f7a058a0fbf4e15fc99a8de91671fb2d5
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44033171"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a><span data-ttu-id="d7b1b-102">Configurando os Serviços de informação da internet 7.0 para o Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d7b1b-102">Configuring Internet Information Services 7.0 for Windows Communication Foundation</span></span>

<span data-ttu-id="d7b1b-103">Serviços de informações da Internet (IIS) 7.0 tem um design modular que permite que você instale seletivamente os componentes que são necessários.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-103">Internet Information Services (IIS) 7.0 has a modular design that allows you to selectively install components that are required.</span></span> <span data-ttu-id="d7b1b-104">Esse design se baseia na tecnologia componentização controlado por manifesto novo introduzida no [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d7b1b-104">This design is based on the new manifest-driven componentization technology introduced in [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="d7b1b-105">Há mais de 40 componentes de recurso autônomo do IIS 7.0 que pode ser instalado de forma independente.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-105">There are more than 40 standalone feature components of IIS 7.0 that can be installed independently.</span></span> <span data-ttu-id="d7b1b-106">Isso permite que os profissionais de TI personalizar facilmente a instalação conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-106">This allows IT professionals to easily customize the installation as required.</span></span> <span data-ttu-id="d7b1b-107">Este tópico discute como configurar o IIS 7.0 para uso com o Windows Communication Foundation (WCF) e determinar quais componentes são necessários.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-107">This topic discusses how to configure IIS 7.0 for use with Windows Communication Foundation (WCF) and determine which components are required.</span></span>

## <a name="minimal-installation-installing-was"></a><span data-ttu-id="d7b1b-108">Instalação mínima: A instalação do WAS</span><span class="sxs-lookup"><span data-stu-id="d7b1b-108">Minimal Installation: Installing WAS</span></span>
 <span data-ttu-id="d7b1b-109">A instalação mínima do pacote completo do IIS 7.0 é instalar o serviço de ativação de processos do Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="d7b1b-109">The minimal installation of the whole IIS 7.0 package is to install the Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="d7b1b-110">FOI é um recurso autônomo e é o único recurso do IIS 7.0 que está disponível para todos os [!INCLUDE[wv](../../../../includes/wv-md.md)] sistemas operacionais (Home Basic, Home Premium, Business e Ultimate e Enterprise).</span><span class="sxs-lookup"><span data-stu-id="d7b1b-110">WAS is a standalone feature and it is the only feature from the IIS 7.0 that is available for all [!INCLUDE[wv](../../../../includes/wv-md.md)] operating systems (Home Basic, Home Premium, Business, and Ultimate and Enterprise).</span></span>

 <span data-ttu-id="d7b1b-111">No painel de controle, clique em **programas** e, em seguida, clique em **ativar ou desativar recursos do Windows ativar** que está listado no **programas e recursos**, o componente WAS é mostrado no lista, como mostra a ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-111">From the Control Panel, click **Programs** and then click **Turn Windows features on or off** which is listed under **Programs and Features**, the WAS component is shown in the list as in the following illustration.</span></span>

 <span data-ttu-id="d7b1b-112">![Recursos de ativar ou desativar o diálogo](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span><span class="sxs-lookup"><span data-stu-id="d7b1b-112">![Turn Features On or Off Dialog](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span></span>

 <span data-ttu-id="d7b1b-113">Esse recurso tem os seguintes subcomponentes:</span><span class="sxs-lookup"><span data-stu-id="d7b1b-113">This feature has the following sub-components:</span></span>

-   <span data-ttu-id="d7b1b-114">Ambiente .NET</span><span class="sxs-lookup"><span data-stu-id="d7b1b-114">.NET Environment</span></span>

-   <span data-ttu-id="d7b1b-115">APIs de configuração</span><span class="sxs-lookup"><span data-stu-id="d7b1b-115">Configuration APIs</span></span>

-   <span data-ttu-id="d7b1b-116">Modelo de processo</span><span class="sxs-lookup"><span data-stu-id="d7b1b-116">Process Model</span></span>

 <span data-ttu-id="d7b1b-117">Se você selecionar o nó raiz do WAS, somente o **modelo de processo** subnó é marcada por padrão.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-117">If you select the root node of WAS, only the **Process Model** sub-node is checked by default.</span></span> <span data-ttu-id="d7b1b-118">Observe que a instalação você está instalando WAS, apenas porque não há suporte para um servidor Web.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-118">Please note that with this installation you are only installing WAS, because there is no support for a Web server.</span></span>

 <span data-ttu-id="d7b1b-119">Para tornar o WCF ou qualquer trabalho de aplicativo do ASP.NET, verifique as **ambiente .NET** caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-119">To make WCF or any ASP.NET application work, check the **.NET Environment** checkbox.</span></span> <span data-ttu-id="d7b1b-120">Isso significa que todos os componentes do WAS são necessários para tornar o WCF e ASP.NET para funcionar bem.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-120">This means that all of WAS components are required to make WCF and ASP.NET to work well.</span></span> <span data-ttu-id="d7b1b-121">Eles são verificados automaticamente depois de instalar qualquer um desses componentes.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-121">These are automatically checked once you install any of those components.</span></span>

## <a name="iis-70-default-installation"></a><span data-ttu-id="d7b1b-122">IIS 7.0: Instalação padrão</span><span class="sxs-lookup"><span data-stu-id="d7b1b-122">IIS 7.0: Default Installation</span></span>
 <span data-ttu-id="d7b1b-123">Verificando a **serviços de informações da Internet** recurso, alguns de nós subpropriedades são verificados automaticamente, conforme mostrado na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-123">By checking the **Internet Information Services** feature, some of the sub-nodes are automatically checked as shown in the following illustration.</span></span>

 <span data-ttu-id="d7b1b-124">![Configurações padrão para recursos do IIS 7.0](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span><span class="sxs-lookup"><span data-stu-id="d7b1b-124">![Default settings for IIS 7.0 features](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span></span>

 <span data-ttu-id="d7b1b-125">Isso é a instalação padrão do IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-125">This is the default installation of IIS 7.0.</span></span> <span data-ttu-id="d7b1b-126">Com essa instalação, você pode usar o IIS 7.0 para conteúdo estático do serviço (como páginas HTML e outros tipos de conteúdo).</span><span class="sxs-lookup"><span data-stu-id="d7b1b-126">With this installation, you can use IIS 7.0 to service static content (such as HTML pages and other content).</span></span> <span data-ttu-id="d7b1b-127">No entanto, é possível executar aplicativos ASP.NET ou CGI ou hospedar serviços WCF.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-127">However, you cannot run ASP.NET or CGI applications or host WCF services.</span></span>

## <a name="iis-70-installation-with-aspnet-support"></a><span data-ttu-id="d7b1b-128">IIS 7.0: Instalação com suporte do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d7b1b-128">IIS 7.0: Installation with ASP.NET Support</span></span>
 <span data-ttu-id="d7b1b-129">Você deve instalar o ASP.NET para fazer com que o ASP.NET funcionar no IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-129">You must install ASP.NET to make ASP.NET work on IIS 7.0.</span></span> <span data-ttu-id="d7b1b-130">Depois de verificar **ASP.NET**, sua tela deve ser semelhante a ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-130">After checking **ASP.NET**, your screen should look like the following illustration.</span></span>

 <span data-ttu-id="d7b1b-131">![As configurações necessárias do Asp.NET](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span><span class="sxs-lookup"><span data-stu-id="d7b1b-131">![Asp.NET required settings](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span></span>

 <span data-ttu-id="d7b1b-132">Isso é o ambiente mínima para aplicativos WCF e ASP.NET funcionar no IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-132">This is the minimal environment for both WCF and ASP.NET applications to work in IIS 7.0.</span></span>

## <a name="iis-70-installation-with-iis-60-compatibility-components"></a><span data-ttu-id="d7b1b-133">IIS 7.0: Instalação com componentes de compatibilidade 6.0 do IIS</span><span class="sxs-lookup"><span data-stu-id="d7b1b-133">IIS 7.0: Installation with IIS 6.0 Compatibility Components</span></span>
 <span data-ttu-id="d7b1b-134">Ao instalar o IIS 7.0 em um sistema com o Visual Studio 2005 ou alguns outros scripts de automação ou ferramentas (como Adsutil. vbs) que configuram aplicativos virtuais que usam a API de Metabase do IIS 6.0, certifique-se de que você verifique o IIS 6.0 **as ferramentas de script**.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-134">When installing IIS 7.0 on a system with Visual Studio 2005 or some other automation scripts or tools (such as Adsutil.vbs) that configure virtual applications that use IIS 6.0 Metabase API, ensure that you check the IIS 6.0 **Scripting Tools**.</span></span> <span data-ttu-id="d7b1b-135">Isso verifica automaticamente os outros nós do IIS 6.0 subpropriedades **compatibilidade com gerenciamento**.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-135">This automatically checks the other sub-nodes of IIS 6.0 **Management Compatibility**.</span></span> <span data-ttu-id="d7b1b-136">A ilustração a seguir mostra a tela depois que isso é feito:</span><span class="sxs-lookup"><span data-stu-id="d7b1b-136">The following illustration shows the screen after this is done:</span></span>

 <span data-ttu-id="d7b1b-137">![Configurações de compatibilidade do IIS 6.0 gerenciamento](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span><span class="sxs-lookup"><span data-stu-id="d7b1b-137">![IIS 6.0 Management Compatibility Settings](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span></span>

 <span data-ttu-id="d7b1b-138">Com esta instalação, você tem tudo que é necessário usar recursos do IIS 7.0, ASP.NET e WCF e exemplos disponíveis na Web.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-138">With this installation, you have everything required to use IIS 7.0, ASP.NET and WCF features and samples available on the Web.</span></span>

## <a name="request-limits"></a><span data-ttu-id="d7b1b-139">Limites de solicitações</span><span class="sxs-lookup"><span data-stu-id="d7b1b-139">Request Limits</span></span>
 <span data-ttu-id="d7b1b-140">Na [!INCLUDE[wv](../../../../includes/wv-md.md)] com o valor padrão do IIS 7 da `maxUri` e `maxQueryStringSize` configurações foram alteradas.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-140">On [!INCLUDE[wv](../../../../includes/wv-md.md)] with IIS 7 the default value of the `maxUri` and `maxQueryStringSize` settings have been changed.</span></span> <span data-ttu-id="d7b1b-141">Por padrão, a filtragem de solicitações no IIS 7.0 permite que um comprimento de URL de 4096 caracteres e um comprimento de cadeia de caracteres de consulta de 2048 caracteres.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-141">By default, request filtering in IIS 7.0 allows a URL length of 4096 characters and a query string length of 2048 characters.</span></span> <span data-ttu-id="d7b1b-142">Para alterar esses padrões adicione o seguinte XML ao seu arquivo App. config.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-142">To change these defaults add the following XML to your App.config file.</span></span>

 `<system.webServer>`

 `<security>`

 `<requestFiltering>`

 `<requestLimits maxUrl="8192" maxQueryString="8192" />`

 `</requestFiltering>`

 `</security>`

 `</system.webServer>`

## <a name="see-also"></a><span data-ttu-id="d7b1b-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7b1b-143">See Also</span></span>

- [<span data-ttu-id="d7b1b-144">Arquitetura de ativação WAS</span><span class="sxs-lookup"><span data-stu-id="d7b1b-144">WAS Activation Architecture</span></span>](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)
- [<span data-ttu-id="d7b1b-145">Configurando o WAS para utilização com o WCF</span><span class="sxs-lookup"><span data-stu-id="d7b1b-145">Configuring WAS for Use with WCF</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [<span data-ttu-id="d7b1b-146">Como instalar e configurar os componentes de ativação do WCF</span><span class="sxs-lookup"><span data-stu-id="d7b1b-146">How to: Install and Configure WCF Activation Components</span></span>](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)
- [<span data-ttu-id="d7b1b-147">Recursos de hospedagem do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="d7b1b-147">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
