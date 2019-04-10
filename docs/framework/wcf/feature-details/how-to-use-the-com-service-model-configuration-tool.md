---
title: 'Como: usar a ferramenta de configuração do modelo de serviço COM+'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
ms.openlocfilehash: 5b330a727c0a4a20de13f43fd2844d0b745e5060
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322583"
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a><span data-ttu-id="72e06-102">Como: usar a ferramenta de configuração do modelo de serviço COM+</span><span class="sxs-lookup"><span data-stu-id="72e06-102">How to: Use the COM+ Service Model Configuration Tool</span></span>
<span data-ttu-id="72e06-103">Depois que você tiver selecionado um modo de hospedagem apropriado, use a ferramenta de linha de comando Configuração de Modelo de Serviço COM+ (ComSvcConfig.exe) para configurar as interfaces de aplicativo que serão expostas como serviços Web.</span><span class="sxs-lookup"><span data-stu-id="72e06-103">Once you have selected an appropriate hosting mode, use the COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) to configure the application interfaces that will be exposed as Web services.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72e06-104">Você deve ser administrador no computador para executar as tarefas a seguir.</span><span class="sxs-lookup"><span data-stu-id="72e06-104">You must be an administrator on the machine to perform any of the following tasks.</span></span>  
  
 <span data-ttu-id="72e06-105">Ao usar ComSvcConfig.exe em um computador com Windows 7 para configurar um serviço Web para usar a versão mais recente do modelo de serviço (atualmente v4.5), execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="72e06-105">When using ComSvcConfig.exe on a Windows 7 machine to configure a web service to use the latest service model version (currently v4.5), perform the following steps:</span></span>  
  
1. <span data-ttu-id="72e06-106">Defina a chave do registro `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` para um valor DWORD de 0x00000001</span><span class="sxs-lookup"><span data-stu-id="72e06-106">Set the registry key  `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` to a DWORD value of 0x00000001</span></span>  
  
2. <span data-ttu-id="72e06-107">Executar comsvcconfig.exe</span><span class="sxs-lookup"><span data-stu-id="72e06-107">Run comsvcconfig.exe</span></span>  
  
3. <span data-ttu-id="72e06-108">Reverter a chave do Registro adicionada na etapa 1 de volta para o seu valor original, ou excluí-la se não existia.</span><span class="sxs-lookup"><span data-stu-id="72e06-108">Revert the registry key added in step 1 back to its original value, or delete it if did not exist.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="72e06-109">Reverter essa chave de Registro é importante.</span><span class="sxs-lookup"><span data-stu-id="72e06-109">Reverting this registry key is important.</span></span> <span data-ttu-id="72e06-110">Essa é uma chave de compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="72e06-110">This is a compatibility key.</span></span> <span data-ttu-id="72e06-111">Não reverter essa alteração pode causar problemas com outros aplicativos .NET que são executados no computador).</span><span class="sxs-lookup"><span data-stu-id="72e06-111">Not reverting this change may cause issues with other .NET applications running on the machine).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="72e06-112">Ao usar ComSvcConfig.exe /install em um computador com Windows 8 uma caixa de diálogo é exibida informando que "um aplicativo em seu computador precisa ter o seguinte recurso do Windows: .NET Framework 3.5 (inclui .NET 2.0 e o .NET 3.0" se o .NET Framework 3.5 não está instalado.</span><span class="sxs-lookup"><span data-stu-id="72e06-112">When using ComSvcConfig.exe  /install on a Windows 8 machine a dialog is displayed stating "An app on your PC needs the following Windows feature: .NET Framework 3.5 (includes .NET 2.0 and .NET 3.0" if .NET Framework 3.5 is not installed.</span></span> <span data-ttu-id="72e06-113">Essa caixa de diálogo pode ser ignorada.</span><span class="sxs-lookup"><span data-stu-id="72e06-113">This dialog may be ignored.</span></span> <span data-ttu-id="72e06-114">Como alternativa, você pode definir a chave do Registro OnlyUseLatestCLR para um valor DWORD de 0x00000001</span><span class="sxs-lookup"><span data-stu-id="72e06-114">Alternatively you can sed the OnlyUseLatestCLR registry key to a DWORD value of 0x00000001</span></span>  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a><span data-ttu-id="72e06-115">Para adicionar uma interface para o conjunto de interfaces que devem ser expostos como serviços Web, usando o modo de hospedagem COM+</span><span class="sxs-lookup"><span data-stu-id="72e06-115">To add an interface to the set of interfaces that are to be exposed as Web services, using the COM+ hosting mode</span></span>  
  
-   <span data-ttu-id="72e06-116">Execute ComSvcConfig usando as opções `/install` e `/hosting:complus`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="72e06-116">Run ComSvcConfig using the `/install` and `/hosting:complus` options, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
    ```  
  
     <span data-ttu-id="72e06-117">O comando adiciona a interface `IFinances` do componente `ItemOrders.IFinancial` (do aplicativo OnlineStore COM+) ao conjunto de interfaces que serão expostas como serviços Web.</span><span class="sxs-lookup"><span data-stu-id="72e06-117">The command adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="72e06-118">O serviço usa o modo de hospedagem COM+ e, portanto, exige a ativação explícita do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="72e06-118">The service uses the COM+ hosting mode and therefore requires explicit application activation.</span></span>  
  
     <span data-ttu-id="72e06-119">Embora o caractere de asterisco curinga (\*) possa ser usado para o componente e a interface, evite usá-lo porque você pode querer expor apenas a funcionalidade selecionada como um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="72e06-119">While the wildcard asterisk (\*) character can be used for the component and the interface, avoid using it because you might want to expose only selected functionality as a Web service.</span></span> <span data-ttu-id="72e06-120">Se for executado com uma versão futura desse componente, usar o curinga pode sem querer expor interfaces que podem não terem estado presentes quando a sintaxe de configuração foi determinada.</span><span class="sxs-lookup"><span data-stu-id="72e06-120">If run with a future version of this component, using the wildcard may unintentionally expose interfaces that may not have been present when the configuration syntax was determined.</span></span>  
  
     <span data-ttu-id="72e06-121">A opção /verbose instrui a ferramenta para exibir avisos além dos erros.</span><span class="sxs-lookup"><span data-stu-id="72e06-121">The /verbose option instructs the tool to display warnings in addition to any errors.</span></span>  
  
     <span data-ttu-id="72e06-122">O contrato para o serviço exposto conterá todos os métodos da interface `IFinances`.</span><span class="sxs-lookup"><span data-stu-id="72e06-122">The contract for the exposed service will contain all of the methods from the `IFinances` interface.</span></span>  
  
### <a name="to-add-only-specific-methods-from-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a><span data-ttu-id="72e06-123">Para adicionar somente métodos específicos de uma interface para o conjunto de interfaces que devem ser expostos como serviços Web, usando o modo de hospedagem COM+</span><span class="sxs-lookup"><span data-stu-id="72e06-123">To add only specific methods from an interface to the set of interfaces that are to be exposed as Web services, using the COM+ hosting mode</span></span>  
  
-   <span data-ttu-id="72e06-124">Execute ComSvcConfig usando as opções `/install` e `/hosting:complus` com nomeação explícita dos métodos necessários, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="72e06-124">Run ComSvcConfig using the `/install` and `/hosting:complus` options with explicit naming of the required methods, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose  
    ```  
  
     <span data-ttu-id="72e06-125">O comando só pode adicionar os métodos `Credit` e `Debit` da interface `IFinances` como operações para o contrato de serviço exposto.</span><span class="sxs-lookup"><span data-stu-id="72e06-125">The command adds only the `Credit` and `Debit` methods from the `IFinances` interface as operations to the exposed service contract.</span></span> <span data-ttu-id="72e06-126">Todos os outros métodos na interface serão omitidos do contrato e não estarão acessíveis para os clientes de serviço Web.</span><span class="sxs-lookup"><span data-stu-id="72e06-126">All other methods on the interface will be omitted from the contract and will not be callable from Web service clients.</span></span>  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-web-hosting-mode"></a><span data-ttu-id="72e06-127">Para adicionar uma interface para o conjunto de interfaces que devem ser expostos como serviços Web, usando o modo de hospedagem Web</span><span class="sxs-lookup"><span data-stu-id="72e06-127">To add an interface to the set of interfaces that are to be exposed as Web services, using the Web hosting mode</span></span>  
  
-   <span data-ttu-id="72e06-128">Execute ComSvcConfig usando as opções `/install` e `/hosting:was`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="72e06-128">Run ComSvcConfig using the `/install` option and the `/hosting:was` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose  
    ```  
  
     <span data-ttu-id="72e06-129">O comando adiciona a interface `IStockLevels` no componente `ItemInventory.Warehouse` (do aplicativo OnlineWarehouse COM+) ao conjunto de interfaces que serão expostas como serviços Web.</span><span class="sxs-lookup"><span data-stu-id="72e06-129">The command adds the `IStockLevels` interface on the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="72e06-130">O serviço Web está hospedado no diretório virtual OnlineWarehouse do IIS em vez de no COM+ e, portanto, o aplicativo é ativado automaticamente conforme o necessário.</span><span class="sxs-lookup"><span data-stu-id="72e06-130">The service is Web hosted in the OnlineWarehouse virtual directory of IIS rather than in COM+, and thus the application is automatically activated as required.</span></span>  
  
     <span data-ttu-id="72e06-131">Para usar a configuração no processo hospedada na Web, o aplicativo COM+ deve ser configurado para ser executado como um aplicativo de biblioteca em vez de um aplicativo de servidor usando o console de administração Serviços de Componentes.</span><span class="sxs-lookup"><span data-stu-id="72e06-131">To use the Web-hosted in-process configuration, the COM+ application must be configured to run as a Library application rather than a Server application using the Component Services administration console.</span></span> <span data-ttu-id="72e06-132">Os aplicativos configurados como aplicativos de servidores usam o modo hospedado na Web padrão e implicam em um salto de processo para processar cada solicitação.</span><span class="sxs-lookup"><span data-stu-id="72e06-132">Applications configured as Server applications use the standard Web-hosted mode and incur a process hop to process each request.</span></span>  
  
     <span data-ttu-id="72e06-133">A opção `/mex` adiciona um ponto de extremidade de serviço adicional do Metadata Exchange (MEX) que use o mesmo transporte que o ponto de extremidade do serviço do aplicativo para dar suporte aos clientes que querem recuperar uma definição de contrato do serviço.</span><span class="sxs-lookup"><span data-stu-id="72e06-133">The `/mex` option adds an additional Metadata Exchange (MEX) service endpoint that uses the same transport as the application's service endpoint to support clients that want to retrieve a contract definition from the service.</span></span>  
  
### <a name="to-remove-a-web-service-for-a-specified-interface"></a><span data-ttu-id="72e06-134">Para remover um serviço Web para uma interface especificada</span><span class="sxs-lookup"><span data-stu-id="72e06-134">To remove a Web service for a specified interface</span></span>  
  
-   <span data-ttu-id="72e06-135">Execute ComSvcConfig usando a opção `/uninstall`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="72e06-135">Run ComSvcConfig using the `/uninstall` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus  
    ```  
  
     <span data-ttu-id="72e06-136">O comando remove a interface `IFinances` no componente `ItemOrders.Financial` (do aplicativo OnlineStore COM+).</span><span class="sxs-lookup"><span data-stu-id="72e06-136">The command removes the `IFinances` interface on the `ItemOrders.Financial` component (from the OnlineStore COM+ application).</span></span>  
  
### <a name="to-list-currently-exposed-interfaces"></a><span data-ttu-id="72e06-137">Para listar as interfaces expostas no momento</span><span class="sxs-lookup"><span data-stu-id="72e06-137">To list currently exposed interfaces</span></span>  
  
-   <span data-ttu-id="72e06-138">Execute ComSvcConfig usando a opção `/list`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="72e06-138">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /list  
    ```  
  
     <span data-ttu-id="72e06-139">O comando lista as interfaces expostas no momento, junto com o endereço de correspondência e os detalhes da associação, no escopo do computador local.</span><span class="sxs-lookup"><span data-stu-id="72e06-139">The command lists the currently exposed interfaces, along with the corresponding address and binding details, scoped to the local machine.</span></span>  
  
### <a name="to-list-specific-currently-exposed-interfaces"></a><span data-ttu-id="72e06-140">Para listar as interfaces específicas expostas no momento</span><span class="sxs-lookup"><span data-stu-id="72e06-140">To list specific currently exposed interfaces</span></span>  
  
-   <span data-ttu-id="72e06-141">Execute ComSvcConfig usando a opção `/list`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="72e06-141">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
    ```  
  
     <span data-ttu-id="72e06-142">O comando lista as interfaces hospedadas no host COM+ expostas no momento, junto com o endereço de correspondência e os detalhes da associação, para o aplicativo OnlineStore COM+ no computador local.</span><span class="sxs-lookup"><span data-stu-id="72e06-142">The command lists currently exposed COM+-hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="to-display-help-on-the-options-that-can-be-used-with-the-utility"></a><span data-ttu-id="72e06-143">Para exibir ajuda sobre as opções que podem ser usadas com o utilitário</span><span class="sxs-lookup"><span data-stu-id="72e06-143">To display help on the options that can be used with the utility</span></span>  
  
-   <span data-ttu-id="72e06-144">Executar ComSvcConfig usando a opção /?,</span><span class="sxs-lookup"><span data-stu-id="72e06-144">Run ComSvcConfig using the /?</span></span> <span data-ttu-id="72e06-145">conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="72e06-145">option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /?  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="72e06-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72e06-146">See also</span></span>

- [<span data-ttu-id="72e06-147">Integração com visão geral de aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="72e06-147">Integrating with COM+ Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)
