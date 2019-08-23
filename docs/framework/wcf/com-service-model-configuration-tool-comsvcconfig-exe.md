---
title: Ferramenta de configuração de modelo de serviço COM+ (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 89462d05b9da7fc63bda58955517bfa9f0c50ab9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964198"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a><span data-ttu-id="24bd8-102">Ferramenta de configuração de modelo de serviço COM+ (ComSvcConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="24bd8-102">COM+ Service Model Configuration Tool (ComSvcConfig.exe)</span></span>
<span data-ttu-id="24bd8-103">A ferramenta de linha de comando de configuração do modelo de serviço COM+ (ComSvcConfig. exe) permite que você configure as interfaces COM+ para serem expostas como serviços Web.</span><span class="sxs-lookup"><span data-stu-id="24bd8-103">The COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) enables you to configure COM+ interfaces to be exposed as Web services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24bd8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="24bd8-104">Syntax</span></span>  
  
```  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a><span data-ttu-id="24bd8-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="24bd8-105">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="24bd8-106">Você deve ser um administrador no computador local para usar o ComSvcConfig. exe.</span><span class="sxs-lookup"><span data-stu-id="24bd8-106">You must be an administrator on the local computer to use ComSvcConfig.exe.</span></span>  
  
 <span data-ttu-id="24bd8-107">A ferramenta pode ser encontrada no seguinte local</span><span class="sxs-lookup"><span data-stu-id="24bd8-107">The tool can be found in the following location</span></span>  
  
 <span data-ttu-id="24bd8-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="24bd8-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
 <span data-ttu-id="24bd8-109">Para obter mais informações sobre o ComSvcConfig. exe [, consulte Como: Use a ferramenta](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)de configuração do modelo de serviço com+.</span><span class="sxs-lookup"><span data-stu-id="24bd8-109">For more information about ComSvcConfig.exe, see [How to: Use the COM+ Service Model Configuration Tool](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span></span>  
  
 <span data-ttu-id="24bd8-110">A tabela a seguir descreve os modos que podem ser usados com ComSvcConfig. exe.</span><span class="sxs-lookup"><span data-stu-id="24bd8-110">The following table describes the modes that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="24bd8-111">Opção</span><span class="sxs-lookup"><span data-stu-id="24bd8-111">Option</span></span>|<span data-ttu-id="24bd8-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="24bd8-112">Description</span></span>|  
|------------|-----------------|  
|`install`|<span data-ttu-id="24bd8-113">Instala uma configuração para uma interface COM+ para integração do modelo de serviço.</span><span class="sxs-lookup"><span data-stu-id="24bd8-113">Installs a configuration for a COM+ interface for Service Model integration.</span></span><br /><br /> <span data-ttu-id="24bd8-114">Forma `/i`abreviada.</span><span class="sxs-lookup"><span data-stu-id="24bd8-114">Short form `/i`.</span></span>|  
|`uninstall`|<span data-ttu-id="24bd8-115">Desinstala uma configuração de uma interface COM+ da integração do modelo de serviço.</span><span class="sxs-lookup"><span data-stu-id="24bd8-115">Uninstalls a configuration for a COM+ interface from Service Model integration.</span></span><br /><br /> <span data-ttu-id="24bd8-116">Forma `/u`abreviada.</span><span class="sxs-lookup"><span data-stu-id="24bd8-116">Short form `/u`.</span></span>|  
|`list`|<span data-ttu-id="24bd8-117">Lista informações sobre aplicativos COM+ e componentes que têm interfaces configuradas para integração do modelo de serviço.</span><span class="sxs-lookup"><span data-stu-id="24bd8-117">Lists information about COM+ applications and components that have interfaces that are configured for Service Model integration.</span></span><br /><br /> <span data-ttu-id="24bd8-118">Forma `/l`abreviada.</span><span class="sxs-lookup"><span data-stu-id="24bd8-118">Short form `/l`.</span></span>|  
  
 <span data-ttu-id="24bd8-119">A tabela a seguir descreve os sinalizadores que podem ser usados com ComSvcConfig. exe.</span><span class="sxs-lookup"><span data-stu-id="24bd8-119">The following table describes the flags that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="24bd8-120">Opção</span><span class="sxs-lookup"><span data-stu-id="24bd8-120">Option</span></span>|<span data-ttu-id="24bd8-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="24bd8-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="24bd8-122">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span><span class="sxs-lookup"><span data-stu-id="24bd8-122">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span></span>|<span data-ttu-id="24bd8-123">Especifica o aplicativo COM+ a ser configurado.</span><span class="sxs-lookup"><span data-stu-id="24bd8-123">Specifies the COM+ application to configure.</span></span><br /><br /> <span data-ttu-id="24bd8-124">Forma `/a`abreviada.</span><span class="sxs-lookup"><span data-stu-id="24bd8-124">Short form `/a`.</span></span>|  
|<span data-ttu-id="24bd8-125">`/contract:`&#124; &#124; &#124; Progidid&#124; de ClassID, interface de interface \* \<    \*\></span><span class="sxs-lookup"><span data-stu-id="24bd8-125">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span></span>|<span data-ttu-id="24bd8-126">Especifica o componente e a interface COM+ que serão configurados como o contrato para o serviço.</span><span class="sxs-lookup"><span data-stu-id="24bd8-126">Specifies the COM+ component and interface that will be configured as the contract for the service.</span></span><br /><br /> <span data-ttu-id="24bd8-127">Forma `/c`abreviada.</span><span class="sxs-lookup"><span data-stu-id="24bd8-127">Short form `/c`.</span></span><br /><br /> <span data-ttu-id="24bd8-128">Embora o caractere curinga (\*) possa ser usado quando você especifica os nomes do componente e da interface, é recomendável não usá-lo, pois você pode expor interfaces que não pretendiam.</span><span class="sxs-lookup"><span data-stu-id="24bd8-128">While the wildcard character (\*) can be used when you specify the component and interface names, we recommend that you do not use it, because you might expose interfaces that you did not intend to.</span></span>|  
|<span data-ttu-id="24bd8-129">`/hosting:` \<*complus*  &#124; *was*\></span><span class="sxs-lookup"><span data-stu-id="24bd8-129">`/hosting:` \<*complus*  &#124; *was*\></span></span>|<span data-ttu-id="24bd8-130">Especifica se o modo de hospedagem COM+ ou o modo de hospedagem da Web deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="24bd8-130">Specifies whether to use the COM+ hosting mode or the Web hosting mode.</span></span><br /><br /> <span data-ttu-id="24bd8-131">Forma `/h`abreviada.</span><span class="sxs-lookup"><span data-stu-id="24bd8-131">Short form `/h`.</span></span><br /><br /> <span data-ttu-id="24bd8-132">Usar o modo de hospedagem COM+ requer ativação explícita do aplicativo COM+.</span><span class="sxs-lookup"><span data-stu-id="24bd8-132">Using the COM+ hosting mode requires explicit activation of the COM+ application.</span></span> <span data-ttu-id="24bd8-133">O uso do modo de hospedagem da Web permite que o aplicativo COM+ seja ativado automaticamente conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="24bd8-133">Using the Web hosting mode allows the COM+ application to be automatically activated as required.</span></span> <span data-ttu-id="24bd8-134">Se o aplicativo COM+ for um aplicativo de biblioteca, ele será executado no processo de Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="24bd8-134">If the COM+ application is a library application, it runs in the Internet Information Services (IIS) process.</span></span> <span data-ttu-id="24bd8-135">Se o aplicativo COM+ for um aplicativo de servidor, ele será executado no processo Dllhost. exe.</span><span class="sxs-lookup"><span data-stu-id="24bd8-135">If the COM+ application is a server application, it runs in the Dllhost.exe process.</span></span>|  
|<span data-ttu-id="24bd8-136">`/webSite:` \<*WebsiteName*\></span><span class="sxs-lookup"><span data-stu-id="24bd8-136">`/webSite:` \<*WebsiteName*\></span></span>|<span data-ttu-id="24bd8-137">Especifica o site para hospedagem quando o modo de hospedagem da Web é usado ( `/hosting` consulte o sinalizador).</span><span class="sxs-lookup"><span data-stu-id="24bd8-137">Specifies the Web site for hosting when Web hosting mode is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="24bd8-138">Forma `/w`abreviada.</span><span class="sxs-lookup"><span data-stu-id="24bd8-138">Short form `/w`.</span></span><br /><br /> <span data-ttu-id="24bd8-139">Se nenhum site da Web for especificado, o site padrão será usado.</span><span class="sxs-lookup"><span data-stu-id="24bd8-139">If no Web site is specified, the default Web site is used.</span></span>|  
|<span data-ttu-id="24bd8-140">`/webDirectory:` \<*WebDirectoryName*\></span><span class="sxs-lookup"><span data-stu-id="24bd8-140">`/webDirectory:` \<*WebDirectoryName*\></span></span>|<span data-ttu-id="24bd8-141">Especifica o diretório virtual para hospedagem quando a hospedagem Web é usada (consulte `/hosting` o sinalizador).</span><span class="sxs-lookup"><span data-stu-id="24bd8-141">Specifies the virtual directory for hosting when Web hosting is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="24bd8-142">Forma `/d`abreviada.</span><span class="sxs-lookup"><span data-stu-id="24bd8-142">Short form `/d`.</span></span>|  
|`/mex`|<span data-ttu-id="24bd8-143">Adiciona um ponto de extremidade de serviço de intercâmbio de metadados (MEX) à configuração de serviço padrão para dar suporte a clientes que desejam recuperar uma definição de contrato do serviço.</span><span class="sxs-lookup"><span data-stu-id="24bd8-143">Adds a Metadata Exchange (MEX) service endpoint to the default service configuration to support clients that want to retrieve a contract definition from the service.</span></span><br /><br /> <span data-ttu-id="24bd8-144">Forma `/x`abreviada.</span><span class="sxs-lookup"><span data-stu-id="24bd8-144">Short form `/x`.</span></span>|  
|`/id`|<span data-ttu-id="24bd8-145">Exibe as informações de aplicativo, componente e interface como IDs.</span><span class="sxs-lookup"><span data-stu-id="24bd8-145">Displays the application, component, and interface information as IDs.</span></span><br /><br /> <span data-ttu-id="24bd8-146">Forma `/k`abreviada.</span><span class="sxs-lookup"><span data-stu-id="24bd8-146">Short form `/k`.</span></span>|  
|`/nologo`|<span data-ttu-id="24bd8-147">Impede que o ComSvcConfig. exe exiba seu logotipo.</span><span class="sxs-lookup"><span data-stu-id="24bd8-147">Prevents ComSvcConfig.exe from displaying its logo.</span></span><br /><br /> <span data-ttu-id="24bd8-148">Forma `/n`abreviada.</span><span class="sxs-lookup"><span data-stu-id="24bd8-148">Short form `/n`.</span></span>|  
|`/verbose`|<span data-ttu-id="24bd8-149">Gera todos os avisos ou texto informativo além dos erros encontrados.</span><span class="sxs-lookup"><span data-stu-id="24bd8-149">Outputs all warnings or informational text in addition to any errors encountered.</span></span><br /><br /> <span data-ttu-id="24bd8-150">Forma `/v`abreviada.</span><span class="sxs-lookup"><span data-stu-id="24bd8-150">Short form `/v`.</span></span>|  
|`/help`|<span data-ttu-id="24bd8-151">Exibe a mensagem de uso.</span><span class="sxs-lookup"><span data-stu-id="24bd8-151">Displays the usage message.</span></span><br /><br /> <span data-ttu-id="24bd8-152">Forma `/?`abreviada.</span><span class="sxs-lookup"><span data-stu-id="24bd8-152">Short form `/?`.</span></span>|  
|`/partial`|<span data-ttu-id="24bd8-153">Gera uma configuração de serviço quando a interface especificada inclui uma ou mais assinaturas de método que podem ser expostas.</span><span class="sxs-lookup"><span data-stu-id="24bd8-153">Generates a service configuration when the specified interface includes one or more method signatures that can be exposed.</span></span> <span data-ttu-id="24bd8-154">No momento da inicialização do serviço, os métodos compatíveis aparecem como operações no contrato de serviço, e os métodos não compatíveis são ignorados e estão ausentes do contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="24bd8-154">At service initialization time, compatible methods appear as operations on the service contract, and non-compatible methods are ignored and absent from the service contract.</span></span><br /><br /> <span data-ttu-id="24bd8-155">Se esse sinalizador estiver ausente, a ferramenta não gerará uma configuração de serviço quando a interface especificada incluir um ou mais métodos incompatíveis.</span><span class="sxs-lookup"><span data-stu-id="24bd8-155">If this flag is missing, the tool will not generate a service configuration when the specified interface includes one or more incompatible methods.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="24bd8-156">Exemplos</span><span class="sxs-lookup"><span data-stu-id="24bd8-156">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="24bd8-157">Descrição</span><span class="sxs-lookup"><span data-stu-id="24bd8-157">Description</span></span>  
 <span data-ttu-id="24bd8-158">O exemplo a seguir adiciona `IFinances` a interface `ItemOrders.IFinancial` do componente (do aplicativo OnlineStore com+) ao conjunto de interfaces que são expostas como serviços Web, usando o modo de hospedagem com+.</span><span class="sxs-lookup"><span data-stu-id="24bd8-158">The following example adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that are exposed as Web services, using the COM+ hosting mode.</span></span> <span data-ttu-id="24bd8-159">Todos os avisos serão exibidos além dos erros encontrados.</span><span class="sxs-lookup"><span data-stu-id="24bd8-159">All warnings will be output in addition to any errors encountered.</span></span>  
  
### <a name="code"></a><span data-ttu-id="24bd8-160">Código</span><span class="sxs-lookup"><span data-stu-id="24bd8-160">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a><span data-ttu-id="24bd8-161">Descrição</span><span class="sxs-lookup"><span data-stu-id="24bd8-161">Description</span></span>  
 <span data-ttu-id="24bd8-162">O exemplo a seguir adiciona `IStockLevels` a interface `ItemInventory.Warehouse` do componente (do aplicativo OnlineWarehouse com+) ao conjunto de interfaces que são expostas como serviços Web, usando o modo de hospedagem da Web.</span><span class="sxs-lookup"><span data-stu-id="24bd8-162">The following example adds the `IStockLevels` interface of the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that are exposed as Web services, using the Web hosting mode.</span></span> <span data-ttu-id="24bd8-163">O serviço Web é hospedado na Web no diretório virtual OnlineWarehouse do IIS.</span><span class="sxs-lookup"><span data-stu-id="24bd8-163">The Web service is Web hosted in the OnlineWarehouse virtual directory of IIS.</span></span>  
  
### <a name="code"></a><span data-ttu-id="24bd8-164">Código</span><span class="sxs-lookup"><span data-stu-id="24bd8-164">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a><span data-ttu-id="24bd8-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="24bd8-165">Description</span></span>  
 <span data-ttu-id="24bd8-166">O exemplo a seguir remove `IFinances` a interface `ItemOrders.Financial` do componente (do aplicativo OnlineStore com+) do conjunto de interfaces que são expostas como serviços Web.</span><span class="sxs-lookup"><span data-stu-id="24bd8-166">The following example removes the `IFinances` interface of the `ItemOrders.Financial` component (from the OnlineStore COM+ application) from the set of interfaces that are exposed as Web services.</span></span>  
  
### <a name="code"></a><span data-ttu-id="24bd8-167">Código</span><span class="sxs-lookup"><span data-stu-id="24bd8-167">Code</span></span>  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a><span data-ttu-id="24bd8-168">Descrição</span><span class="sxs-lookup"><span data-stu-id="24bd8-168">Description</span></span>  
 <span data-ttu-id="24bd8-169">O exemplo a seguir lista as interfaces hospedadas do COM+ atualmente expostas, juntamente com os detalhes de endereço e associação correspondentes, para o aplicativo OnlineStore COM+ no computador local.</span><span class="sxs-lookup"><span data-stu-id="24bd8-169">The following example lists currently exposed COM+ hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="code"></a><span data-ttu-id="24bd8-170">Código</span><span class="sxs-lookup"><span data-stu-id="24bd8-170">Code</span></span>  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a><span data-ttu-id="24bd8-171">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24bd8-171">See also</span></span>

- [<span data-ttu-id="24bd8-172">Como: Usar a ferramenta de configuração do modelo de serviço COM+</span><span class="sxs-lookup"><span data-stu-id="24bd8-172">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
