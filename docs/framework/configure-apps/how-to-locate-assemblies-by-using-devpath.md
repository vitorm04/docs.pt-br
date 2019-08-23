---
title: 'Como: Localizar assemblies usando DEVPATH'
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 6fa864f814d6a9ce04f2bce92c61cd0075ab5145
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912995"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a><span data-ttu-id="9d5d0-102">Como: Localizar assemblies usando DEVPATH</span><span class="sxs-lookup"><span data-stu-id="9d5d0-102">How to: Locate Assemblies by Using DEVPATH</span></span>
<span data-ttu-id="9d5d0-103">Os desenvolvedores podem querer ter certeza de que um assembly compartilhado que está compilando funciona corretamente com vários aplicativos.</span><span class="sxs-lookup"><span data-stu-id="9d5d0-103">Developers might want to make sure that a shared assembly they are building works correctly with multiple applications.</span></span> <span data-ttu-id="9d5d0-104">Em vez de colocar continuamente o assembly no cache de assembly global durante o ciclo de desenvolvimento, o desenvolvedor pode criar uma variável de ambiente DEVPATH que aponta para o diretório de saída da compilação para o assembly.</span><span class="sxs-lookup"><span data-stu-id="9d5d0-104">Instead of continually putting the assembly in the global assembly cache during the development cycle, the developer can create a DEVPATH environment variable that points to the build output directory for the assembly.</span></span>  
  
 <span data-ttu-id="9d5d0-105">Por exemplo, suponha que você esteja criando um assembly compartilhado chamado MySharedAssembly e o diretório de saída seja C:\MySharedAssembly\Debug.</span><span class="sxs-lookup"><span data-stu-id="9d5d0-105">For example, assume that you are building a shared assembly called MySharedAssembly and the output directory is C:\MySharedAssembly\Debug.</span></span> <span data-ttu-id="9d5d0-106">Você pode colocar C:\MySharedAssembly\Debug na variável DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="9d5d0-106">You can put C:\MySharedAssembly\Debug in the DEVPATH variable.</span></span> <span data-ttu-id="9d5d0-107">Em seguida, você deve especificar o elemento de [ \<> developmentmode](./file-schema/runtime/developmentmode-element.md) no arquivo de configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="9d5d0-107">You must then specify the [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) element in the machine configuration file.</span></span> <span data-ttu-id="9d5d0-108">Esse elemento informa ao Common Language Runtime usar DEVPATH para localizar assemblies.</span><span class="sxs-lookup"><span data-stu-id="9d5d0-108">This element tells the common language runtime to use DEVPATH to locate assemblies.</span></span>  
  
 <span data-ttu-id="9d5d0-109">O assembly compartilhado deve ser detectável pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9d5d0-109">The shared assembly must be discoverable by the runtime.</span></span>  <span data-ttu-id="9d5d0-110">Para especificar um diretório privado para resolver referências de assembly, use o elemento [ \<> codebase](./file-schema/runtime/codebase-element.md) ou [ \<o elemento > de investigação](./file-schema/runtime/probing-element.md) em um arquivo de configuração, conforme descrito em [especificando o local de um assembly](specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="9d5d0-110">To specify a private directory for resolving assembly references use the [\<codeBase> Element](./file-schema/runtime/codebase-element.md) or [\<probing> Element](./file-schema/runtime/probing-element.md) in a configuration file, as described in [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>  <span data-ttu-id="9d5d0-111">Você também pode colocar o assembly em um subdiretório do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d5d0-111">You can also put the assembly in a subdirectory of the application directory.</span></span> <span data-ttu-id="9d5d0-112">Para saber mais, confira [Como o tempo de execução localiza os assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="9d5d0-112">For more information, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9d5d0-113">Esse é um recurso avançado, destinado apenas ao desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="9d5d0-113">This is an advanced feature, intended only for development.</span></span>  
  
 <span data-ttu-id="9d5d0-114">O exemplo a seguir mostra como fazer com que o tempo de execução procure por assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="9d5d0-114">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d5d0-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d5d0-115">Example</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="9d5d0-116">Essa configuração assume como padrão false.</span><span class="sxs-lookup"><span data-stu-id="9d5d0-116">This setting defaults to false.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9d5d0-117">Use essa configuração somente no momento do desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="9d5d0-117">Use this setting only at development time.</span></span> <span data-ttu-id="9d5d0-118">O tempo de execução não verifica as versões em assemblies de nome forte encontrados no DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="9d5d0-118">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="9d5d0-119">Ele simplesmente usa o primeiro assembly que encontra.</span><span class="sxs-lookup"><span data-stu-id="9d5d0-119">It simply uses the first assembly it finds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d5d0-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d5d0-120">See also</span></span>

- [<span data-ttu-id="9d5d0-121">Configurando aplicativos usando arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="9d5d0-121">Configuring Apps by using Configuration Files</span></span>](index.md)
