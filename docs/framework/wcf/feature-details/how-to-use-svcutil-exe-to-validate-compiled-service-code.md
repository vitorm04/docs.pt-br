---
title: Como usar o Svcutil.exe para validar o código de serviço compilado
ms.date: 03/30/2017
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
ms.openlocfilehash: 6f2064c696e3186c3208a7e57dc51655056d23ea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595343"
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a><span data-ttu-id="e6693-102">Como usar o Svcutil.exe para validar o código de serviço compilado</span><span class="sxs-lookup"><span data-stu-id="e6693-102">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>
<span data-ttu-id="e6693-103">Você pode usar a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) para detectar erros em implementações de serviço e configurações sem hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="e6693-103">You can use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to detect errors in service implementations and configurations without hosting the service.</span></span>  
  
### <a name="to-validate-a-service"></a><span data-ttu-id="e6693-104">Para validar um serviço</span><span class="sxs-lookup"><span data-stu-id="e6693-104">To validate a service</span></span>  
  
1. <span data-ttu-id="e6693-105">Compile seu serviço em um arquivo executável e em um ou mais assemblies dependentes.</span><span class="sxs-lookup"><span data-stu-id="e6693-105">Compile your service into an executable file and one or more dependent assemblies.</span></span>  
  
2. <span data-ttu-id="e6693-106">Abrir um prompt de comando do SDK</span><span class="sxs-lookup"><span data-stu-id="e6693-106">Open an SDK command prompt</span></span>  
  
3. <span data-ttu-id="e6693-107">No prompt de comando, inicie a ferramenta svcutil. exe usando o formato a seguir.</span><span class="sxs-lookup"><span data-stu-id="e6693-107">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span> <span data-ttu-id="e6693-108">Para obter mais informações sobre os vários parâmetros, consulte o Validationsection de serviço do tópico [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="e6693-108">For more information on the various parameters, see the Service Validationsection of the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) topic.</span></span>  
  
    ```console
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="e6693-109">Você deve usar a `/serviceName` opção para indicar o nome da configuração do serviço que deseja validar.</span><span class="sxs-lookup"><span data-stu-id="e6693-109">You must use the `/serviceName` option to indicate the configuration name of the service you want to validate.</span></span>  
  
     <span data-ttu-id="e6693-110">O `assemblyPath` argumento especifica o caminho para o arquivo executável para o serviço e um ou mais assemblies que contêm os tipos de serviço a serem validados.</span><span class="sxs-lookup"><span data-stu-id="e6693-110">The `assemblyPath` argument specifies the path to the executable file for the service and one or more assemblies that contain the service types to be validated.</span></span> <span data-ttu-id="e6693-111">O assembly executável deve ter um arquivo de configuração associado para fornecer a configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="e6693-111">The executable assembly must have an associated configuration file to provide the service configuration.</span></span> <span data-ttu-id="e6693-112">Você pode usar curingas de linha de comando padrão para fornecer vários assemblies.</span><span class="sxs-lookup"><span data-stu-id="e6693-112">You can use standard command-line wildcards to provide multiple assemblies.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6693-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e6693-113">Example</span></span>  
 <span data-ttu-id="e6693-114">O comando a seguir o serviço myServiceName implementado no arquivo executável myservicehost. exe.</span><span class="sxs-lookup"><span data-stu-id="e6693-114">The following command the service myServiceName implemented in the myServiceHost.exe executable file.</span></span>  <span data-ttu-id="e6693-115">O arquivo de configuração para o serviço (myservicehost. exe. config) é carregado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e6693-115">The configuration file for the service (myServiceHost.exe.config) is automatically loaded.</span></span>  
  
```console  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6693-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6693-116">See also</span></span>

- [<span data-ttu-id="e6693-117">Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="e6693-117">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
