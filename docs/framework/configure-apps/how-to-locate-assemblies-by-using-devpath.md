---
title: 'Como: Localizar assemblies usando DEVPATH'
description: Teste se um assembly compartilhado funciona corretamente com muitos aplicativos no .NET usando um arquivo de configuração de computador XML e a variável de ambiente DEVPATH.
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 50b61eedddabd660b1834565a61738f460ae9ff9
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105373"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a><span data-ttu-id="d9bcb-103">Como: Localizar assemblies usando DEVPATH</span><span class="sxs-lookup"><span data-stu-id="d9bcb-103">How to: Locate Assemblies by Using DEVPATH</span></span>
<span data-ttu-id="d9bcb-104">Os desenvolvedores podem querer ter certeza de que um assembly compartilhado que está compilando funciona corretamente com vários aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d9bcb-104">Developers might want to make sure that a shared assembly they are building works correctly with multiple applications.</span></span> <span data-ttu-id="d9bcb-105">Em vez de colocar continuamente o assembly no cache de assembly global durante o ciclo de desenvolvimento, o desenvolvedor pode criar uma variável de ambiente DEVPATH que aponta para o diretório de saída da compilação para o assembly.</span><span class="sxs-lookup"><span data-stu-id="d9bcb-105">Instead of continually putting the assembly in the global assembly cache during the development cycle, the developer can create a DEVPATH environment variable that points to the build output directory for the assembly.</span></span>  
  
 <span data-ttu-id="d9bcb-106">Por exemplo, suponha que você esteja criando um assembly compartilhado chamado MySharedAssembly e o diretório de saída seja C:\MySharedAssembly\Debug.</span><span class="sxs-lookup"><span data-stu-id="d9bcb-106">For example, assume that you are building a shared assembly called MySharedAssembly and the output directory is C:\MySharedAssembly\Debug.</span></span> <span data-ttu-id="d9bcb-107">Você pode colocar C:\MySharedAssembly\Debug na variável DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="d9bcb-107">You can put C:\MySharedAssembly\Debug in the DEVPATH variable.</span></span> <span data-ttu-id="d9bcb-108">Em seguida, você deve especificar o [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) elemento no arquivo de configuração da máquina.</span><span class="sxs-lookup"><span data-stu-id="d9bcb-108">You must then specify the [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) element in the machine configuration file.</span></span> <span data-ttu-id="d9bcb-109">Esse elemento informa ao Common Language Runtime usar DEVPATH para localizar assemblies.</span><span class="sxs-lookup"><span data-stu-id="d9bcb-109">This element tells the common language runtime to use DEVPATH to locate assemblies.</span></span>  
  
 <span data-ttu-id="d9bcb-110">O assembly compartilhado deve ser detectável pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d9bcb-110">The shared assembly must be discoverable by the runtime.</span></span>  <span data-ttu-id="d9bcb-111">Para especificar um diretório privado para resolver referências de assembly, use o [ \<codeBase> elemento](./file-schema/runtime/codebase-element.md) ou [ \<probing> elemento](./file-schema/runtime/probing-element.md) em um arquivo de configuração, conforme descrito em [especificando o local de um assembly](specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="d9bcb-111">To specify a private directory for resolving assembly references use the [\<codeBase> Element](./file-schema/runtime/codebase-element.md) or [\<probing> Element](./file-schema/runtime/probing-element.md) in a configuration file, as described in [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>  <span data-ttu-id="d9bcb-112">Você também pode colocar o assembly em um subdiretório do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d9bcb-112">You can also put the assembly in a subdirectory of the application directory.</span></span> <span data-ttu-id="d9bcb-113">Para saber mais, confira [Como o runtime localiza os assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="d9bcb-113">For more information, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9bcb-114">Esse é um recurso avançado, destinado apenas ao desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="d9bcb-114">This is an advanced feature, intended only for development.</span></span>  
  
 <span data-ttu-id="d9bcb-115">O exemplo a seguir mostra como fazer com que o tempo de execução procure por assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="d9bcb-115">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9bcb-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d9bcb-116">Example</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="d9bcb-117">Essa configuração assume como padrão false.</span><span class="sxs-lookup"><span data-stu-id="d9bcb-117">This setting defaults to false.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9bcb-118">Use essa configuração somente no momento do desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="d9bcb-118">Use this setting only at development time.</span></span> <span data-ttu-id="d9bcb-119">O tempo de execução não verifica as versões em assemblies de nome forte encontrados no DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="d9bcb-119">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="d9bcb-120">Ele simplesmente usa o primeiro assembly que encontra.</span><span class="sxs-lookup"><span data-stu-id="d9bcb-120">It simply uses the first assembly it finds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9bcb-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="d9bcb-121">See also</span></span>

- [<span data-ttu-id="d9bcb-122">Configurando aplicativos usando arquivos de configuração </span><span class="sxs-lookup"><span data-stu-id="d9bcb-122">Configuring Apps by using Configuration Files</span></span>](index.md)
