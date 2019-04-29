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
ms.openlocfilehash: 5c4041f42b0a9d1d1e4bc8438e662911534daa42
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775824"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a><span data-ttu-id="972a3-102">Como: Localizar assemblies usando DEVPATH</span><span class="sxs-lookup"><span data-stu-id="972a3-102">How to: Locate Assemblies by Using DEVPATH</span></span>
<span data-ttu-id="972a3-103">Talvez os desenvolvedores queiram certificar-se de que um assembly compartilhado que elas estão criando funciona corretamente com vários aplicativos.</span><span class="sxs-lookup"><span data-stu-id="972a3-103">Developers might want to make sure that a shared assembly they are building works correctly with multiple applications.</span></span> <span data-ttu-id="972a3-104">Em vez de continuamente colocar o assembly no cache de assembly global durante o ciclo de desenvolvimento, o desenvolvedor pode criar uma variável de ambiente DEVPATH que aponta para o diretório de saída de compilação para o assembly.</span><span class="sxs-lookup"><span data-stu-id="972a3-104">Instead of continually putting the assembly in the global assembly cache during the development cycle, the developer can create a DEVPATH environment variable that points to the build output directory for the assembly.</span></span>  
  
 <span data-ttu-id="972a3-105">Por exemplo, suponha que você esteja criando um assembly compartilhado chamado MySharedAssembly e o diretório de saída é C:\MySharedAssembly\Debug.</span><span class="sxs-lookup"><span data-stu-id="972a3-105">For example, assume that you are building a shared assembly called MySharedAssembly and the output directory is C:\MySharedAssembly\Debug.</span></span> <span data-ttu-id="972a3-106">Você pode colocar C:\MySharedAssembly\Debug na variável DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="972a3-106">You can put C:\MySharedAssembly\Debug in the DEVPATH variable.</span></span> <span data-ttu-id="972a3-107">Em seguida, você deve especificar o [ \<developmentMode >](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) elemento no arquivo de configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="972a3-107">You must then specify the [\<developmentMode>](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) element in the machine configuration file.</span></span> <span data-ttu-id="972a3-108">Esse elemento informa o common language runtime usar DEVPATH para localizar assemblies.</span><span class="sxs-lookup"><span data-stu-id="972a3-108">This element tells the common language runtime to use DEVPATH to locate assemblies.</span></span>  
  
 <span data-ttu-id="972a3-109">O assembly compartilhado deve ser detectável pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="972a3-109">The shared assembly must be discoverable by the runtime.</span></span>  <span data-ttu-id="972a3-110">Para especificar um diretório particular para resolver referências de assembly usam o [ \<codeBase > elemento](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) ou [ \<probing > elemento](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) em um arquivo de configuração, conforme descrito em [Especificando o local do Assembly](../../../docs/framework/configure-apps/specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="972a3-110">To specify a private directory for resolving assembly references use the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) or [\<probing> Element](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) in a configuration file, as described in [Specifying an Assembly's Location](../../../docs/framework/configure-apps/specify-assembly-location.md).</span></span>  <span data-ttu-id="972a3-111">Você também pode colocar o assembly em um subdiretório do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="972a3-111">You can also put the assembly in a subdirectory of the application directory.</span></span> <span data-ttu-id="972a3-112">Para saber mais, confira [Como o tempo de execução localiza os assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="972a3-112">For more information, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="972a3-113">Isso é um recurso avançado, destinado apenas para desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="972a3-113">This is an advanced feature, intended only for development.</span></span>  
  
 <span data-ttu-id="972a3-114">O exemplo a seguir mostra como fazer com que o tempo de execução pesquisa dos assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="972a3-114">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="972a3-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="972a3-115">Example</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="972a3-116">Essa configuração padrão é false.</span><span class="sxs-lookup"><span data-stu-id="972a3-116">This setting defaults to false.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="972a3-117">Use essa configuração somente em tempo de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="972a3-117">Use this setting only at development time.</span></span> <span data-ttu-id="972a3-118">O tempo de execução não verifica as versões de assemblies de nome forte encontrados no DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="972a3-118">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="972a3-119">Ela simplesmente usa o assembly primeiro que ele localiza.</span><span class="sxs-lookup"><span data-stu-id="972a3-119">It simply uses the first assembly it finds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="972a3-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="972a3-120">See also</span></span>

- [<span data-ttu-id="972a3-121">Configurando aplicativos usando arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="972a3-121">Configuring Apps by using Configuration Files</span></span>](index.md)
