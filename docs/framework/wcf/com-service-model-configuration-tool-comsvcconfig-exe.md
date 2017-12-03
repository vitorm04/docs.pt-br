---
title: "Ferramenta de configuração de modelo de serviço COM+ (ComSvcConfig.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 322268f5b11a5078545ae120440f91d327d6a615
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a><span data-ttu-id="824ea-102">Ferramenta de configuração de modelo de serviço COM+ (ComSvcConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="824ea-102">COM+ Service Model Configuration Tool (ComSvcConfig.exe)</span></span>
<span data-ttu-id="824ea-103">A ferramenta de linha de comando de configuração de modelo de serviço COM+ (ComSvcConfig.exe) permite que você configure COM+ interfaces a serem expostas como serviços da Web.</span><span class="sxs-lookup"><span data-stu-id="824ea-103">The COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) enables you to configure COM+ interfaces to be exposed as Web services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="824ea-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="824ea-104">Syntax</span></span>  
  
```  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a><span data-ttu-id="824ea-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="824ea-105">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="824ea-106">Você deve ser um administrador no computador local para usar ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="824ea-106">You must be an administrator on the local computer to use ComSvcConfig.exe.</span></span>  
  
 <span data-ttu-id="824ea-107">A ferramenta pode ser encontrada no seguinte local</span><span class="sxs-lookup"><span data-stu-id="824ea-107">The tool can be found in the following location</span></span>  
  
 <span data-ttu-id="824ea-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Foundation\ de comunicação</span><span class="sxs-lookup"><span data-stu-id="824ea-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span></span>  
  
 <span data-ttu-id="824ea-109">Para obter mais informações sobre ComSvcConfig.exe, consulte [como: usar a ferramenta Configuração do modelo de COM+ serviço](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span><span class="sxs-lookup"><span data-stu-id="824ea-109">For more information about ComSvcConfig.exe, see [How to: Use the COM+ Service Model Configuration Tool](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span></span>  
  
 <span data-ttu-id="824ea-110">A tabela a seguir descreve os modos que podem ser usados com ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="824ea-110">The following table describes the modes that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="824ea-111">Opção</span><span class="sxs-lookup"><span data-stu-id="824ea-111">Option</span></span>|<span data-ttu-id="824ea-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="824ea-112">Description</span></span>|  
|------------|-----------------|  
|`install`|<span data-ttu-id="824ea-113">Instala uma configuração para uma interface para integração com o modelo de serviço COM+.</span><span class="sxs-lookup"><span data-stu-id="824ea-113">Installs a configuration for a COM+ interface for Service Model integration.</span></span><br /><br /> <span data-ttu-id="824ea-114">Forma abreviada `/i`.</span><span class="sxs-lookup"><span data-stu-id="824ea-114">Short form `/i`.</span></span>|  
|`uninstall`|<span data-ttu-id="824ea-115">Desinstala uma configuração para uma interface COM+ de integração de modelo de serviço.</span><span class="sxs-lookup"><span data-stu-id="824ea-115">Uninstalls a configuration for a COM+ interface from Service Model integration.</span></span><br /><br /> <span data-ttu-id="824ea-116">Forma abreviada `/u`.</span><span class="sxs-lookup"><span data-stu-id="824ea-116">Short form `/u`.</span></span>|  
|`list`|<span data-ttu-id="824ea-117">Lista informações sobre aplicativos e componentes que têm interfaces que estão configurados para integração com o modelo de serviço.</span><span class="sxs-lookup"><span data-stu-id="824ea-117">Lists information about COM+ applications and components that have interfaces that are configured for Service Model integration.</span></span><br /><br /> <span data-ttu-id="824ea-118">Forma abreviada `/l`.</span><span class="sxs-lookup"><span data-stu-id="824ea-118">Short form `/l`.</span></span>|  
  
 <span data-ttu-id="824ea-119">A tabela a seguir descreve os sinalizadores que podem ser usados com ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="824ea-119">The following table describes the flags that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="824ea-120">Opção</span><span class="sxs-lookup"><span data-stu-id="824ea-120">Option</span></span>|<span data-ttu-id="824ea-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="824ea-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="824ea-122">`/application:`\< *ApplicationID* &#124; *ApplicationName*\></span><span class="sxs-lookup"><span data-stu-id="824ea-122">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span></span>|<span data-ttu-id="824ea-123">Especifica o aplicativo COM+ a configurar.</span><span class="sxs-lookup"><span data-stu-id="824ea-123">Specifies the COM+ application to configure.</span></span><br /><br /> <span data-ttu-id="824ea-124">Forma abreviada `/a`.</span><span class="sxs-lookup"><span data-stu-id="824ea-124">Short form `/a`.</span></span>|  
|<span data-ttu-id="824ea-125">`/contract:`\< *ClassID* &#124; *ProgID* &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124;\*\></span><span class="sxs-lookup"><span data-stu-id="824ea-125">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span></span>|<span data-ttu-id="824ea-126">Especifica o componente COM+ e a interface que será configurado como o contrato para o serviço.</span><span class="sxs-lookup"><span data-stu-id="824ea-126">Specifies the COM+ component and interface that will be configured as the contract for the service.</span></span><br /><br /> <span data-ttu-id="824ea-127">Forma abreviada `/c`.</span><span class="sxs-lookup"><span data-stu-id="824ea-127">Short form `/c`.</span></span><br /><br /> <span data-ttu-id="824ea-128">Embora o caractere curinga (\*) pode ser usado quando você especificar os nomes de componente e interface, recomendamos que você não usá-lo, porque você poderá expor interfaces que você não pretendia.</span><span class="sxs-lookup"><span data-stu-id="824ea-128">While the wildcard character (\*) can be used when you specify the component and interface names, we recommend that you do not use it, because you might expose interfaces that you did not intend to.</span></span>|  
|<span data-ttu-id="824ea-129">`/hosting:`\< *complus* &#124; *foi*\></span><span class="sxs-lookup"><span data-stu-id="824ea-129">`/hosting:` \<*complus*  &#124; *was*\></span></span>|<span data-ttu-id="824ea-130">Especifica se deve usar o modo ou o modo de hospedagem da Web de hospedagem COM+.</span><span class="sxs-lookup"><span data-stu-id="824ea-130">Specifies whether to use the COM+ hosting mode or the Web hosting mode.</span></span><br /><br /> <span data-ttu-id="824ea-131">Forma abreviada `/h`.</span><span class="sxs-lookup"><span data-stu-id="824ea-131">Short form `/h`.</span></span><br /><br /> <span data-ttu-id="824ea-132">Usando o COM+ hospedar modo exige a ativação explícita do aplicativo COM+.</span><span class="sxs-lookup"><span data-stu-id="824ea-132">Using the COM+ hosting mode requires explicit activation of the COM+ application.</span></span> <span data-ttu-id="824ea-133">Usar o modo de hospedagem permite que o aplicativo COM+ seja ativado automaticamente como Web necessária.</span><span class="sxs-lookup"><span data-stu-id="824ea-133">Using the Web hosting mode allows the COM+ application to be automatically activated as required.</span></span> <span data-ttu-id="824ea-134">Se o aplicativo COM+ é um aplicativo de biblioteca, ele é executado no processo do Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="824ea-134">If the COM+ application is a library application, it runs in the Internet Information Services (IIS) process.</span></span> <span data-ttu-id="824ea-135">Se o aplicativo COM+ é um aplicativo de servidor, ele é executado no processo Dllhost.exe.</span><span class="sxs-lookup"><span data-stu-id="824ea-135">If the COM+ application is a server application, it runs in the Dllhost.exe process.</span></span>|  
|<span data-ttu-id="824ea-136">`/webSite:`\< *WebsiteName*\></span><span class="sxs-lookup"><span data-stu-id="824ea-136">`/webSite:` \<*WebsiteName*\></span></span>|<span data-ttu-id="824ea-137">Especifica o site da Web para hospedar quando o modo de hospedagem na Web é usado (consulte o `/hosting` sinalizador).</span><span class="sxs-lookup"><span data-stu-id="824ea-137">Specifies the Web site for hosting when Web hosting mode is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="824ea-138">Forma abreviada `/w`.</span><span class="sxs-lookup"><span data-stu-id="824ea-138">Short form `/w`.</span></span><br /><br /> <span data-ttu-id="824ea-139">Se nenhum site é especificado, o site padrão será usado.</span><span class="sxs-lookup"><span data-stu-id="824ea-139">If no Web site is specified, the default Web site is used.</span></span>|  
|<span data-ttu-id="824ea-140">`/webDirectory:`\< *WebDirectoryName*\></span><span class="sxs-lookup"><span data-stu-id="824ea-140">`/webDirectory:` \<*WebDirectoryName*\></span></span>|<span data-ttu-id="824ea-141">Especifica o diretório virtual para hospedagem de hospedagem na Web é usada (consulte o `/hosting` sinalizador).</span><span class="sxs-lookup"><span data-stu-id="824ea-141">Specifies the virtual directory for hosting when Web hosting is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="824ea-142">Forma abreviada `/d`.</span><span class="sxs-lookup"><span data-stu-id="824ea-142">Short form `/d`.</span></span>|  
|`/mex`|<span data-ttu-id="824ea-143">Adiciona um ponto de extremidade do serviço de troca de metadados (MEX) para a configuração de serviço padrão para oferecer suporte a clientes que deseja recuperar de uma definição de contrato do serviço.</span><span class="sxs-lookup"><span data-stu-id="824ea-143">Adds a Metadata Exchange (MEX) service endpoint to the default service configuration to support clients that want to retrieve a contract definition from the service.</span></span><br /><br /> <span data-ttu-id="824ea-144">Forma abreviada `/x`.</span><span class="sxs-lookup"><span data-stu-id="824ea-144">Short form `/x`.</span></span>|  
|`/id`|<span data-ttu-id="824ea-145">Exibe o aplicativo, componente e informações de interface como IDs.</span><span class="sxs-lookup"><span data-stu-id="824ea-145">Displays the application, component, and interface information as IDs.</span></span><br /><br /> <span data-ttu-id="824ea-146">Forma abreviada `/k`.</span><span class="sxs-lookup"><span data-stu-id="824ea-146">Short form `/k`.</span></span>|  
|`/nologo`|<span data-ttu-id="824ea-147">Impede que ComSvcConfig.exe seu logotipo.</span><span class="sxs-lookup"><span data-stu-id="824ea-147">Prevents ComSvcConfig.exe from displaying its logo.</span></span><br /><br /> <span data-ttu-id="824ea-148">Forma abreviada `/n`.</span><span class="sxs-lookup"><span data-stu-id="824ea-148">Short form `/n`.</span></span>|  
|`/verbose`|<span data-ttu-id="824ea-149">Gera todos os avisos ou texto informativo, além de todos os erros encontrados.</span><span class="sxs-lookup"><span data-stu-id="824ea-149">Outputs all warnings or informational text in addition to any errors encountered.</span></span><br /><br /> <span data-ttu-id="824ea-150">Forma abreviada `/v`.</span><span class="sxs-lookup"><span data-stu-id="824ea-150">Short form `/v`.</span></span>|  
|`/help`|<span data-ttu-id="824ea-151">Exibe a mensagem de uso.</span><span class="sxs-lookup"><span data-stu-id="824ea-151">Displays the usage message.</span></span><br /><br /> <span data-ttu-id="824ea-152">Forma abreviada `/?`.</span><span class="sxs-lookup"><span data-stu-id="824ea-152">Short form `/?`.</span></span>|  
|`/partial`|<span data-ttu-id="824ea-153">Gera uma configuração de serviço quando a interface especificada inclui uma ou mais assinaturas de método que podem ser expostas.</span><span class="sxs-lookup"><span data-stu-id="824ea-153">Generates a service configuration when the specified interface includes one or more method signatures that can be exposed.</span></span> <span data-ttu-id="824ea-154">No momento da inicialização de serviço, métodos compatíveis aparecem como operações no contrato de serviço, e os métodos de não compatível são ignorados e ausentes ao contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="824ea-154">At service initialization time, compatible methods appear as operations on the service contract, and non-compatible methods are ignored and absent from the service contract.</span></span><br /><br /> <span data-ttu-id="824ea-155">Se esse sinalizador estiver ausente, a ferramenta não gerará uma configuração de serviço quando a interface especificada inclui um ou mais métodos incompatíveis.</span><span class="sxs-lookup"><span data-stu-id="824ea-155">If this flag is missing, the tool will not generate a service configuration when the specified interface includes one or more incompatible methods.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="824ea-156">Exemplos</span><span class="sxs-lookup"><span data-stu-id="824ea-156">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="824ea-157">Descrição</span><span class="sxs-lookup"><span data-stu-id="824ea-157">Description</span></span>  
 <span data-ttu-id="824ea-158">O exemplo a seguir adiciona o `IFinances` interface do `ItemOrders.IFinancial` componente (a partir do aplicativo COM+ OnlineStore) para o conjunto de interfaces que são expostas como serviços da Web, usando o modo de hospedagem COM+.</span><span class="sxs-lookup"><span data-stu-id="824ea-158">The following example adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that are exposed as Web services, using the COM+ hosting mode.</span></span> <span data-ttu-id="824ea-159">Todos os avisos serão gerados além de todos os erros encontrados.</span><span class="sxs-lookup"><span data-stu-id="824ea-159">All warnings will be output in addition to any errors encountered.</span></span>  
  
### <a name="code"></a><span data-ttu-id="824ea-160">Código</span><span class="sxs-lookup"><span data-stu-id="824ea-160">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a><span data-ttu-id="824ea-161">Descrição</span><span class="sxs-lookup"><span data-stu-id="824ea-161">Description</span></span>  
 <span data-ttu-id="824ea-162">O exemplo a seguir adiciona o `IStockLevels` interface do `ItemInventory.Warehouse` componente (a partir do aplicativo COM+ OnlineWarehouse) para o conjunto de interfaces que são expostas como serviços da Web, usando o modo de hospedagem na Web.</span><span class="sxs-lookup"><span data-stu-id="824ea-162">The following example adds the `IStockLevels` interface of the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that are exposed as Web services, using the Web hosting mode.</span></span> <span data-ttu-id="824ea-163">O serviço Web é que Web hospedada no diretório virtual OnlineWarehouse do IIS.</span><span class="sxs-lookup"><span data-stu-id="824ea-163">The Web service is Web hosted in the OnlineWarehouse virtual directory of IIS.</span></span>  
  
### <a name="code"></a><span data-ttu-id="824ea-164">Código</span><span class="sxs-lookup"><span data-stu-id="824ea-164">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a><span data-ttu-id="824ea-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="824ea-165">Description</span></span>  
 <span data-ttu-id="824ea-166">O exemplo a seguir remove o `IFinances` interface do `ItemOrders.Financial` componente (a partir do aplicativo COM+ OnlineStore) do conjunto de interfaces que são expostas como serviços da Web.</span><span class="sxs-lookup"><span data-stu-id="824ea-166">The following example removes the `IFinances` interface of the `ItemOrders.Financial` component (from the OnlineStore COM+ application) from the set of interfaces that are exposed as Web services.</span></span>  
  
### <a name="code"></a><span data-ttu-id="824ea-167">Código</span><span class="sxs-lookup"><span data-stu-id="824ea-167">Code</span></span>  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a><span data-ttu-id="824ea-168">Descrição</span><span class="sxs-lookup"><span data-stu-id="824ea-168">Description</span></span>  
 <span data-ttu-id="824ea-169">A exemplo a seguir lista atualmente expostos hospedados pelo COM+ interfaces, juntamente com o endereço correspondente e os detalhes de associação, para o aplicativo COM+ OnlineStore no computador local.</span><span class="sxs-lookup"><span data-stu-id="824ea-169">The following example lists currently exposed COM+ hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="code"></a><span data-ttu-id="824ea-170">Código</span><span class="sxs-lookup"><span data-stu-id="824ea-170">Code</span></span>  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a><span data-ttu-id="824ea-171">Consulte também</span><span class="sxs-lookup"><span data-stu-id="824ea-171">See Also</span></span>  
 [<span data-ttu-id="824ea-172">Como: usar a ferramenta de configuração de modelo de serviço COM+</span><span class="sxs-lookup"><span data-stu-id="824ea-172">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
