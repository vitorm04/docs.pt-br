---
title: Configurando os Serviços de informação da internet 7.0 para o Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 6343049e2a21b06965a8c7851d891303a49c82b5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597560"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a><span data-ttu-id="38407-102">Configurando os Serviços de informação da internet 7.0 para o Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="38407-102">Configuring Internet Information Services 7.0 for Windows Communication Foundation</span></span>

<span data-ttu-id="38407-103">O Serviços de Informações da Internet (IIS) 7,0 tem um design modular que permite que você instale seletivamente os componentes necessários.</span><span class="sxs-lookup"><span data-stu-id="38407-103">Internet Information Services (IIS) 7.0 has a modular design that allows you to selectively install components that are required.</span></span> <span data-ttu-id="38407-104">Esse design se baseia na nova tecnologia de componentização orientada por manifesto introduzida no Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="38407-104">This design is based on the new manifest-driven componentization technology introduced in Windows Vista.</span></span> <span data-ttu-id="38407-105">Há mais de 40 componentes de recursos autônomos do IIS 7,0 que podem ser instalados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="38407-105">There are more than 40 standalone feature components of IIS 7.0 that can be installed independently.</span></span> <span data-ttu-id="38407-106">Isso permite que os profissionais de ti personalizem facilmente a instalação conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="38407-106">This allows IT professionals to easily customize the installation as required.</span></span> <span data-ttu-id="38407-107">Este tópico discute como configurar o IIS 7,0 para uso com o Windows Communication Foundation (WCF) e determinar quais componentes são necessários.</span><span class="sxs-lookup"><span data-stu-id="38407-107">This topic discusses how to configure IIS 7.0 for use with Windows Communication Foundation (WCF) and determine which components are required.</span></span>

## <a name="minimal-installation-installing-was"></a><span data-ttu-id="38407-108">Instalação mínima: a instalação do foi</span><span class="sxs-lookup"><span data-stu-id="38407-108">Minimal Installation: Installing WAS</span></span>
 <span data-ttu-id="38407-109">A instalação mínima de todo o pacote do IIS 7,0 é instalar o WAS (serviço de ativação de processos do Windows).</span><span class="sxs-lookup"><span data-stu-id="38407-109">The minimal installation of the whole IIS 7.0 package is to install the Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="38407-110">O WAS é um recurso autônomo e é o único recurso do IIS 7,0 que está disponível para todos os sistemas operacionais Windows Vista (Home Basic, Home Premium, Business e Ultimate e Enterprise).</span><span class="sxs-lookup"><span data-stu-id="38407-110">WAS is a standalone feature and it is the only feature from the IIS 7.0 that is available for all Windows Vista operating systems (Home Basic, Home Premium, Business, and Ultimate and Enterprise).</span></span>

 <span data-ttu-id="38407-111">No painel de controle, clique em **programas** e, em seguida, clique em **Ativar ou desativar recursos do Windows** , que está listado em **programas e recursos**, o componente was é mostrado na lista como na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="38407-111">From the Control Panel, click **Programs** and then click **Turn Windows features on or off** which is listed under **Programs and Features**, the WAS component is shown in the list as in the following illustration.</span></span>

 <span data-ttu-id="38407-112">![Caixa de diálogo de ativar ou desativar recursos](media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span><span class="sxs-lookup"><span data-stu-id="38407-112">![Turn Features On or Off Dialog](media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span></span>

 <span data-ttu-id="38407-113">Este recurso tem os seguintes subcomponentes:</span><span class="sxs-lookup"><span data-stu-id="38407-113">This feature has the following sub-components:</span></span>

- <span data-ttu-id="38407-114">Ambiente .NET</span><span class="sxs-lookup"><span data-stu-id="38407-114">.NET Environment</span></span>

- <span data-ttu-id="38407-115">APIs de configuração</span><span class="sxs-lookup"><span data-stu-id="38407-115">Configuration APIs</span></span>

- <span data-ttu-id="38407-116">Modelo de processo</span><span class="sxs-lookup"><span data-stu-id="38407-116">Process Model</span></span>

 <span data-ttu-id="38407-117">Se você selecionar o nó raiz do WAS, somente o subnó do **modelo de processo** será verificado por padrão.</span><span class="sxs-lookup"><span data-stu-id="38407-117">If you select the root node of WAS, only the **Process Model** sub-node is checked by default.</span></span> <span data-ttu-id="38407-118">Observe que, com essa instalação, você está instalando o WAS, porque não há suporte para um servidor Web.</span><span class="sxs-lookup"><span data-stu-id="38407-118">Please note that with this installation you are only installing WAS, because there is no support for a Web server.</span></span>

 <span data-ttu-id="38407-119">Para fazer com que o WCF ou qualquer aplicativo ASP.NET funcione, marque a caixa de seleção **ambiente .net** .</span><span class="sxs-lookup"><span data-stu-id="38407-119">To make WCF or any ASP.NET application work, check the **.NET Environment** checkbox.</span></span> <span data-ttu-id="38407-120">Isso significa que todos os componentes do WAS são necessários para fazer com que o WCF e o ASP.NET funcionem bem.</span><span class="sxs-lookup"><span data-stu-id="38407-120">This means that all of WAS components are required to make WCF and ASP.NET to work well.</span></span> <span data-ttu-id="38407-121">Eles são verificados automaticamente após a instalação de qualquer um desses componentes.</span><span class="sxs-lookup"><span data-stu-id="38407-121">These are automatically checked once you install any of those components.</span></span>

## <a name="iis-70-default-installation"></a><span data-ttu-id="38407-122">IIS 7,0: instalação padrão</span><span class="sxs-lookup"><span data-stu-id="38407-122">IIS 7.0: Default Installation</span></span>
 <span data-ttu-id="38407-123">Ao verificar o recurso **serviços de informações da Internet** , alguns dos subnós são automaticamente verificados, conforme mostrado na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="38407-123">By checking the **Internet Information Services** feature, some of the sub-nodes are automatically checked as shown in the following illustration.</span></span>

 <span data-ttu-id="38407-124">![Configurações padrão para recursos do IIS 7.0](media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span><span class="sxs-lookup"><span data-stu-id="38407-124">![Default settings for IIS 7.0 features](media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span></span>

 <span data-ttu-id="38407-125">Esta é a instalação padrão do IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="38407-125">This is the default installation of IIS 7.0.</span></span> <span data-ttu-id="38407-126">Com essa instalação, você pode usar o IIS 7,0 para serviço de conteúdo estático (como páginas HTML e outro conteúdo).</span><span class="sxs-lookup"><span data-stu-id="38407-126">With this installation, you can use IIS 7.0 to service static content (such as HTML pages and other content).</span></span> <span data-ttu-id="38407-127">No entanto, você não pode executar aplicativos ASP.NET ou CGI nem hospedar serviços WCF.</span><span class="sxs-lookup"><span data-stu-id="38407-127">However, you cannot run ASP.NET or CGI applications or host WCF services.</span></span>

## <a name="iis-70-installation-with-aspnet-support"></a><span data-ttu-id="38407-128">IIS 7,0: instalação com suporte a ASP.NET</span><span class="sxs-lookup"><span data-stu-id="38407-128">IIS 7.0: Installation with ASP.NET Support</span></span>
 <span data-ttu-id="38407-129">Você deve instalar o ASP.NET para fazer com que o ASP.NET funcione no IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="38407-129">You must install ASP.NET to make ASP.NET work on IIS 7.0.</span></span> <span data-ttu-id="38407-130">Depois de verificar **ASP.net**, sua tela deve ser parecida com a ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="38407-130">After checking **ASP.NET**, your screen should look like the following illustration.</span></span>

 <span data-ttu-id="38407-131">![Configurações exigidas pelo ASP.NET](media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span><span class="sxs-lookup"><span data-stu-id="38407-131">![Asp.NET required settings](media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span></span>

 <span data-ttu-id="38407-132">Esse é o ambiente mínimo para que os aplicativos WCF e ASP.NET funcionem no IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="38407-132">This is the minimal environment for both WCF and ASP.NET applications to work in IIS 7.0.</span></span>

## <a name="iis-70-installation-with-iis-60-compatibility-components"></a><span data-ttu-id="38407-133">IIS 7,0: instalação com componentes de compatibilidade do IIS 6,0</span><span class="sxs-lookup"><span data-stu-id="38407-133">IIS 7.0: Installation with IIS 6.0 Compatibility Components</span></span>
 <span data-ttu-id="38407-134">Ao instalar o IIS 7,0 em um sistema com o Visual Studio 2005 ou outros scripts ou ferramentas de automação (como Adsutil. vbs) que configuram aplicativos virtuais que usam a API de metabase do IIS 6,0, verifique as **ferramentas de script**do IIS 6,0.</span><span class="sxs-lookup"><span data-stu-id="38407-134">When installing IIS 7.0 on a system with Visual Studio 2005 or some other automation scripts or tools (such as Adsutil.vbs) that configure virtual applications that use IIS 6.0 Metabase API, ensure that you check the IIS 6.0 **Scripting Tools**.</span></span> <span data-ttu-id="38407-135">Isso verifica automaticamente os outros subnós da **compatibilidade de gerenciamento**do IIS 6,0.</span><span class="sxs-lookup"><span data-stu-id="38407-135">This automatically checks the other sub-nodes of IIS 6.0 **Management Compatibility**.</span></span> <span data-ttu-id="38407-136">A ilustração a seguir mostra a tela depois que isso é feito:</span><span class="sxs-lookup"><span data-stu-id="38407-136">The following illustration shows the screen after this is done:</span></span>

 <span data-ttu-id="38407-137">![Configurações de compatibilidade de gerenciamento do IIS 6.0](media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span><span class="sxs-lookup"><span data-stu-id="38407-137">![IIS 6.0 Management Compatibility Settings](media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span></span>

 <span data-ttu-id="38407-138">Com essa instalação, você tem tudo o que é necessário para usar os recursos do IIS 7,0, ASP.NET e WCF e exemplos disponíveis na Web.</span><span class="sxs-lookup"><span data-stu-id="38407-138">With this installation, you have everything required to use IIS 7.0, ASP.NET and WCF features and samples available on the Web.</span></span>

## <a name="request-limits"></a><span data-ttu-id="38407-139">Limites de solicitações</span><span class="sxs-lookup"><span data-stu-id="38407-139">Request Limits</span></span>
 <span data-ttu-id="38407-140">No Windows Vista com IIS 7, o valor padrão das `maxUri` `maxQueryStringSize` configurações e foi alterado.</span><span class="sxs-lookup"><span data-stu-id="38407-140">On Windows Vista with IIS 7 the default value of the `maxUri` and `maxQueryStringSize` settings have been changed.</span></span> <span data-ttu-id="38407-141">Por padrão, a filtragem de solicitações no IIS 7,0 permite um comprimento de URL de 4096 caracteres e um comprimento de cadeia de caracteres de consulta de 2048 caracteres.</span><span class="sxs-lookup"><span data-stu-id="38407-141">By default, request filtering in IIS 7.0 allows a URL length of 4096 characters and a query string length of 2048 characters.</span></span> <span data-ttu-id="38407-142">Para alterar esses padrões, adicione o seguinte XML ao seu arquivo app. config.</span><span class="sxs-lookup"><span data-stu-id="38407-142">To change these defaults add the following XML to your App.config file.</span></span>

```xml
 <system.webServer>
    <security>
        <requestFiltering>
            <requestLimits maxUrl="8192" maxQueryString="8192" />
        </requestFiltering>
    </security>
 </system.webServer>
 ```

## <a name="see-also"></a><span data-ttu-id="38407-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38407-143">See also</span></span>

- [<span data-ttu-id="38407-144">Arquitetura de ativação do WAS</span><span class="sxs-lookup"><span data-stu-id="38407-144">WAS Activation Architecture</span></span>](was-activation-architecture.md)
- [<span data-ttu-id="38407-145">Configurar o WAS para uso com o WCF</span><span class="sxs-lookup"><span data-stu-id="38407-145">Configuring WAS for Use with WCF</span></span>](configuring-the-wpa--service-for-use-with-wcf.md)
- [<span data-ttu-id="38407-146">Como instalar e configurar os componentes de ativação do WCF</span><span class="sxs-lookup"><span data-stu-id="38407-146">How to: Install and Configure WCF Activation Components</span></span>](how-to-install-and-configure-wcf-activation-components.md)
- <span data-ttu-id="38407-147">[Recursos de hospedagem do Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="38407-147">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
