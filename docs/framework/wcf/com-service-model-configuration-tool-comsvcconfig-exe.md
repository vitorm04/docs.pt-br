---
title: Ferramenta de configuração de modelo de serviço COM+ (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 6d0967355e64640e0fd5c81f04a5bf4f33c7b3f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608834"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a><span data-ttu-id="488fc-102">Ferramenta de configuração de modelo de serviço COM+ (ComSvcConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="488fc-102">COM+ Service Model Configuration Tool (ComSvcConfig.exe)</span></span>
<span data-ttu-id="488fc-103">A ferramenta de linha de comando de configuração de modelo de serviço COM+ (ComSvcConfig.exe) permite que você configure interfaces COM+ deve ser exposta como serviços da Web.</span><span class="sxs-lookup"><span data-stu-id="488fc-103">The COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) enables you to configure COM+ interfaces to be exposed as Web services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="488fc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="488fc-104">Syntax</span></span>  
  
```  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a><span data-ttu-id="488fc-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="488fc-105">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="488fc-106">Você deve ser um administrador no computador local para usar ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="488fc-106">You must be an administrator on the local computer to use ComSvcConfig.exe.</span></span>  
  
 <span data-ttu-id="488fc-107">A ferramenta pode ser encontrada no seguinte local</span><span class="sxs-lookup"><span data-stu-id="488fc-107">The tool can be found in the following location</span></span>  
  
 <span data-ttu-id="488fc-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span><span class="sxs-lookup"><span data-stu-id="488fc-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span></span>  
  
 <span data-ttu-id="488fc-109">Para obter mais informações sobre ComSvcConfig.exe, consulte [como: Use a ferramenta de configuração de modelo de serviço COM+](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span><span class="sxs-lookup"><span data-stu-id="488fc-109">For more information about ComSvcConfig.exe, see [How to: Use the COM+ Service Model Configuration Tool](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span></span>  
  
 <span data-ttu-id="488fc-110">A tabela a seguir descreve os modos que podem ser usados com ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="488fc-110">The following table describes the modes that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="488fc-111">Opção</span><span class="sxs-lookup"><span data-stu-id="488fc-111">Option</span></span>|<span data-ttu-id="488fc-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="488fc-112">Description</span></span>|  
|------------|-----------------|  
|`install`|<span data-ttu-id="488fc-113">Instala uma configuração para uma interface COM+ para integração com o modelo de serviço.</span><span class="sxs-lookup"><span data-stu-id="488fc-113">Installs a configuration for a COM+ interface for Service Model integration.</span></span><br /><br /> <span data-ttu-id="488fc-114">Forma abreviada `/i`.</span><span class="sxs-lookup"><span data-stu-id="488fc-114">Short form `/i`.</span></span>|  
|`uninstall`|<span data-ttu-id="488fc-115">Desinstala uma configuração para uma interface COM+ de integração do modelo de serviço.</span><span class="sxs-lookup"><span data-stu-id="488fc-115">Uninstalls a configuration for a COM+ interface from Service Model integration.</span></span><br /><br /> <span data-ttu-id="488fc-116">Forma abreviada `/u`.</span><span class="sxs-lookup"><span data-stu-id="488fc-116">Short form `/u`.</span></span>|  
|`list`|<span data-ttu-id="488fc-117">Lista informações sobre aplicativos COM+ e componentes com interfaces que estão configuradas para integração com o modelo de serviço.</span><span class="sxs-lookup"><span data-stu-id="488fc-117">Lists information about COM+ applications and components that have interfaces that are configured for Service Model integration.</span></span><br /><br /> <span data-ttu-id="488fc-118">Forma abreviada `/l`.</span><span class="sxs-lookup"><span data-stu-id="488fc-118">Short form `/l`.</span></span>|  
  
 <span data-ttu-id="488fc-119">A tabela a seguir descreve os sinalizadores que podem ser usados com ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="488fc-119">The following table describes the flags that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="488fc-120">Opção</span><span class="sxs-lookup"><span data-stu-id="488fc-120">Option</span></span>|<span data-ttu-id="488fc-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="488fc-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="488fc-122">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span><span class="sxs-lookup"><span data-stu-id="488fc-122">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span></span>|<span data-ttu-id="488fc-123">Especifica o aplicativo COM+ para configurar.</span><span class="sxs-lookup"><span data-stu-id="488fc-123">Specifies the COM+ application to configure.</span></span><br /><br /> <span data-ttu-id="488fc-124">Forma abreviada `/a`.</span><span class="sxs-lookup"><span data-stu-id="488fc-124">Short form `/a`.</span></span>|  
|<span data-ttu-id="488fc-125">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span><span class="sxs-lookup"><span data-stu-id="488fc-125">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span></span>|<span data-ttu-id="488fc-126">Especifica o componente COM+ e a interface que será configurado como o contrato do serviço.</span><span class="sxs-lookup"><span data-stu-id="488fc-126">Specifies the COM+ component and interface that will be configured as the contract for the service.</span></span><br /><br /> <span data-ttu-id="488fc-127">Forma abreviada `/c`.</span><span class="sxs-lookup"><span data-stu-id="488fc-127">Short form `/c`.</span></span><br /><br /> <span data-ttu-id="488fc-128">Embora o caractere curinga (\*) pode ser usado quando você especifica os nomes de componente e a interface, é recomendável que você não usá-lo, porque você pode expor interfaces que você não pretendia.</span><span class="sxs-lookup"><span data-stu-id="488fc-128">While the wildcard character (\*) can be used when you specify the component and interface names, we recommend that you do not use it, because you might expose interfaces that you did not intend to.</span></span>|  
|<span data-ttu-id="488fc-129">`/hosting:` \<*complus*  &#124; *was*\></span><span class="sxs-lookup"><span data-stu-id="488fc-129">`/hosting:` \<*complus*  &#124; *was*\></span></span>|<span data-ttu-id="488fc-130">Especifica se deve usar o modo ou o modo de hospedagem da Web de hospedagem COM+.</span><span class="sxs-lookup"><span data-stu-id="488fc-130">Specifies whether to use the COM+ hosting mode or the Web hosting mode.</span></span><br /><br /> <span data-ttu-id="488fc-131">Forma abreviada `/h`.</span><span class="sxs-lookup"><span data-stu-id="488fc-131">Short form `/h`.</span></span><br /><br /> <span data-ttu-id="488fc-132">Modo de hospedagem usando o COM+ exige a ativação explícita do aplicativo COM+.</span><span class="sxs-lookup"><span data-stu-id="488fc-132">Using the COM+ hosting mode requires explicit activation of the COM+ application.</span></span> <span data-ttu-id="488fc-133">Usando a Web do modo de hospedagem permite que o aplicativo COM+ a ser ativado automaticamente como necessário.</span><span class="sxs-lookup"><span data-stu-id="488fc-133">Using the Web hosting mode allows the COM+ application to be automatically activated as required.</span></span> <span data-ttu-id="488fc-134">Se o aplicativo COM+ é um aplicativo de biblioteca, ele é executado no processo de serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="488fc-134">If the COM+ application is a library application, it runs in the Internet Information Services (IIS) process.</span></span> <span data-ttu-id="488fc-135">Se o aplicativo COM+ é um aplicativo de servidor, ele é executado no processo de Dllhost.exe.</span><span class="sxs-lookup"><span data-stu-id="488fc-135">If the COM+ application is a server application, it runs in the Dllhost.exe process.</span></span>|  
|<span data-ttu-id="488fc-136">`/webSite:` \<*WebsiteName*\></span><span class="sxs-lookup"><span data-stu-id="488fc-136">`/webSite:` \<*WebsiteName*\></span></span>|<span data-ttu-id="488fc-137">Especifica o site da Web para hospedar quando o modo de hospedagem na Web é usado (consulte a `/hosting` sinalizador).</span><span class="sxs-lookup"><span data-stu-id="488fc-137">Specifies the Web site for hosting when Web hosting mode is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="488fc-138">Forma abreviada `/w`.</span><span class="sxs-lookup"><span data-stu-id="488fc-138">Short form `/w`.</span></span><br /><br /> <span data-ttu-id="488fc-139">Se nenhum site da Web for especificado, o site padrão será usado.</span><span class="sxs-lookup"><span data-stu-id="488fc-139">If no Web site is specified, the default Web site is used.</span></span>|  
|<span data-ttu-id="488fc-140">`/webDirectory:` \<*WebDirectoryName*\></span><span class="sxs-lookup"><span data-stu-id="488fc-140">`/webDirectory:` \<*WebDirectoryName*\></span></span>|<span data-ttu-id="488fc-141">Especifica o diretório virtual para a hospedagem de hospedagem na Web é usado (consulte a `/hosting` sinalizador).</span><span class="sxs-lookup"><span data-stu-id="488fc-141">Specifies the virtual directory for hosting when Web hosting is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="488fc-142">Forma abreviada `/d`.</span><span class="sxs-lookup"><span data-stu-id="488fc-142">Short form `/d`.</span></span>|  
|`/mex`|<span data-ttu-id="488fc-143">Adiciona um ponto de extremidade de serviço de troca de metadados (MEX) à configuração de serviço padrão para dar suporte a clientes que desejam recuperar uma definição de contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="488fc-143">Adds a Metadata Exchange (MEX) service endpoint to the default service configuration to support clients that want to retrieve a contract definition from the service.</span></span><br /><br /> <span data-ttu-id="488fc-144">Forma abreviada `/x`.</span><span class="sxs-lookup"><span data-stu-id="488fc-144">Short form `/x`.</span></span>|  
|`/id`|<span data-ttu-id="488fc-145">Exibe o aplicativo, componente e informações de interface, como IDs.</span><span class="sxs-lookup"><span data-stu-id="488fc-145">Displays the application, component, and interface information as IDs.</span></span><br /><br /> <span data-ttu-id="488fc-146">Forma abreviada `/k`.</span><span class="sxs-lookup"><span data-stu-id="488fc-146">Short form `/k`.</span></span>|  
|`/nologo`|<span data-ttu-id="488fc-147">Impede que ComSvcConfig.exe exibindo seu logotipo.</span><span class="sxs-lookup"><span data-stu-id="488fc-147">Prevents ComSvcConfig.exe from displaying its logo.</span></span><br /><br /> <span data-ttu-id="488fc-148">Forma abreviada `/n`.</span><span class="sxs-lookup"><span data-stu-id="488fc-148">Short form `/n`.</span></span>|  
|`/verbose`|<span data-ttu-id="488fc-149">Gera todos os avisos ou texto informativo, além de todos os erros encontrados.</span><span class="sxs-lookup"><span data-stu-id="488fc-149">Outputs all warnings or informational text in addition to any errors encountered.</span></span><br /><br /> <span data-ttu-id="488fc-150">Forma abreviada `/v`.</span><span class="sxs-lookup"><span data-stu-id="488fc-150">Short form `/v`.</span></span>|  
|`/help`|<span data-ttu-id="488fc-151">Exibe a mensagem de uso.</span><span class="sxs-lookup"><span data-stu-id="488fc-151">Displays the usage message.</span></span><br /><br /> <span data-ttu-id="488fc-152">Forma abreviada `/?`.</span><span class="sxs-lookup"><span data-stu-id="488fc-152">Short form `/?`.</span></span>|  
|`/partial`|<span data-ttu-id="488fc-153">Gera uma configuração de serviço quando a interface especificada inclui uma ou mais assinaturas de método que podem ser expostas.</span><span class="sxs-lookup"><span data-stu-id="488fc-153">Generates a service configuration when the specified interface includes one or more method signatures that can be exposed.</span></span> <span data-ttu-id="488fc-154">No momento da inicialização de serviço, métodos compatíveis aparecem como operações no contrato de serviço, e não-compatíveis com métodos são ignorados e estavam ausentes ao contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="488fc-154">At service initialization time, compatible methods appear as operations on the service contract, and non-compatible methods are ignored and absent from the service contract.</span></span><br /><br /> <span data-ttu-id="488fc-155">Se esse sinalizador estiver ausente, a ferramenta não irá gerar uma configuração de serviço quando a interface especificada inclui um ou mais métodos incompatíveis.</span><span class="sxs-lookup"><span data-stu-id="488fc-155">If this flag is missing, the tool will not generate a service configuration when the specified interface includes one or more incompatible methods.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="488fc-156">Exemplos</span><span class="sxs-lookup"><span data-stu-id="488fc-156">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="488fc-157">Descrição</span><span class="sxs-lookup"><span data-stu-id="488fc-157">Description</span></span>  
 <span data-ttu-id="488fc-158">O exemplo a seguir adiciona o `IFinances` interface da `ItemOrders.IFinancial` componente (do aplicativo aplicativo OnlineStore COM+) ao conjunto de interfaces que são expostas como serviços da Web, usando o modo de hospedagem COM+.</span><span class="sxs-lookup"><span data-stu-id="488fc-158">The following example adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that are exposed as Web services, using the COM+ hosting mode.</span></span> <span data-ttu-id="488fc-159">Todos os avisos serão gerados, além de todos os erros encontrados.</span><span class="sxs-lookup"><span data-stu-id="488fc-159">All warnings will be output in addition to any errors encountered.</span></span>  
  
### <a name="code"></a><span data-ttu-id="488fc-160">Código</span><span class="sxs-lookup"><span data-stu-id="488fc-160">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a><span data-ttu-id="488fc-161">Descrição</span><span class="sxs-lookup"><span data-stu-id="488fc-161">Description</span></span>  
 <span data-ttu-id="488fc-162">O exemplo a seguir adiciona o `IStockLevels` interface da `ItemInventory.Warehouse` componente (a partir do aplicativo OnlineWarehouse COM+) ao conjunto de interfaces que são expostos como serviços Web, usando o modo de host Web.</span><span class="sxs-lookup"><span data-stu-id="488fc-162">The following example adds the `IStockLevels` interface of the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that are exposed as Web services, using the Web hosting mode.</span></span> <span data-ttu-id="488fc-163">O serviço Web é que Web hospedada no diretório virtual OnlineWarehouse do IIS.</span><span class="sxs-lookup"><span data-stu-id="488fc-163">The Web service is Web hosted in the OnlineWarehouse virtual directory of IIS.</span></span>  
  
### <a name="code"></a><span data-ttu-id="488fc-164">Código</span><span class="sxs-lookup"><span data-stu-id="488fc-164">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a><span data-ttu-id="488fc-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="488fc-165">Description</span></span>  
 <span data-ttu-id="488fc-166">O exemplo a seguir remove a `IFinances` interface da `ItemOrders.Financial` componente (do aplicativo OnlineStore COM+ aplicativo) do conjunto de interfaces que são expostas como serviços da Web.</span><span class="sxs-lookup"><span data-stu-id="488fc-166">The following example removes the `IFinances` interface of the `ItemOrders.Financial` component (from the OnlineStore COM+ application) from the set of interfaces that are exposed as Web services.</span></span>  
  
### <a name="code"></a><span data-ttu-id="488fc-167">Código</span><span class="sxs-lookup"><span data-stu-id="488fc-167">Code</span></span>  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a><span data-ttu-id="488fc-168">Descrição</span><span class="sxs-lookup"><span data-stu-id="488fc-168">Description</span></span>  
 <span data-ttu-id="488fc-169">A exemplo a seguir lista expostos atualmente hospedado interfaces COM+, juntamente com o endereço de correspondência e os detalhes da associação, para o aplicativo do aplicativo OnlineStore COM+ no computador local.</span><span class="sxs-lookup"><span data-stu-id="488fc-169">The following example lists currently exposed COM+ hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="code"></a><span data-ttu-id="488fc-170">Código</span><span class="sxs-lookup"><span data-stu-id="488fc-170">Code</span></span>  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a><span data-ttu-id="488fc-171">Consulte também</span><span class="sxs-lookup"><span data-stu-id="488fc-171">See also</span></span>

- [<span data-ttu-id="488fc-172">Como: Use a ferramenta de configuração de modelo de serviço COM+</span><span class="sxs-lookup"><span data-stu-id="488fc-172">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
