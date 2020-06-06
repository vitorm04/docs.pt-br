---
title: Especificando o local de um assembly
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: ead69d1e850050214c15295134c06ff6f66e9760
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "81646026"
---
# <a name="specifying-an-assemblys-location"></a><span data-ttu-id="eab27-102">Especificando o local de um assembly</span><span class="sxs-lookup"><span data-stu-id="eab27-102">Specifying an Assembly's Location</span></span>
<span data-ttu-id="eab27-103">Há duas maneiras de especificar o local de um assembly:</span><span class="sxs-lookup"><span data-stu-id="eab27-103">There are two ways to specify an assembly's location:</span></span>  
  
- <span data-ttu-id="eab27-104">Usando o [\<codeBase>](./file-schema/runtime/codebase-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="eab27-104">Using the [\<codeBase>](./file-schema/runtime/codebase-element.md) element.</span></span>  
  
- <span data-ttu-id="eab27-105">Usando o [\<probing>](./file-schema/runtime/probing-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="eab27-105">Using the [\<probing>](./file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="eab27-106">Você também pode usar a [ferramenta de configuração de .NET Framework (Mscorcfg. msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) para especificar locais de assembly ou especificar locais para o Common Language Runtime investigar para assemblies.</span><span class="sxs-lookup"><span data-stu-id="eab27-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="eab27-107">Usando o \<codeBase> elemento</span><span class="sxs-lookup"><span data-stu-id="eab27-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="eab27-108">Você pode usar o **\<codeBase>** elemento somente em configuração do computador ou em arquivos de política do Publicador que também redirecionem a versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="eab27-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="eab27-109">Quando o tempo de execução determina qual versão de assembly usar, ele aplica a configuração de base do código do arquivo que determina a versão.</span><span class="sxs-lookup"><span data-stu-id="eab27-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="eab27-110">Se nenhuma base de código for indicada, o tempo de execução investigará o assembly da maneira normal.</span><span class="sxs-lookup"><span data-stu-id="eab27-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="eab27-111">Para obter detalhes, consulte [como o tempo de execução localiza assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="eab27-111">For details, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="eab27-112">O exemplo a seguir mostra como especificar o local de um assembly.</span><span class="sxs-lookup"><span data-stu-id="eab27-112">The following example shows how to specify an assembly's location.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <codeBase version="2.0.0.0"  
                   href="http://www.litwareinc.com/myAssembly.dll"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="eab27-113">O atributo **version** é necessário para todos os assemblies de nome forte, mas deve ser omitido para assemblies que não são de nome forte.</span><span class="sxs-lookup"><span data-stu-id="eab27-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="eab27-114">O **\<codeBase>** elemento requer o atributo **href** .</span><span class="sxs-lookup"><span data-stu-id="eab27-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="eab27-115">Você não pode especificar intervalos de versão no **\<codeBase>** elemento.</span><span class="sxs-lookup"><span data-stu-id="eab27-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eab27-116">Se você estiver fornecendo uma dica de base de código para um assembly que não seja de nome forte, a dica deverá apontar para a base do aplicativo ou um subdiretório do diretório base do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eab27-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="eab27-117">Usando o \<probing> elemento</span><span class="sxs-lookup"><span data-stu-id="eab27-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="eab27-118">O tempo de execução localiza assemblies que não têm uma base de código por investigação.</span><span class="sxs-lookup"><span data-stu-id="eab27-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="eab27-119">Para obter mais informações sobre investigação, consulte [como o tempo de execução localiza assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="eab27-119">For more information about probing, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="eab27-120">Você pode usar o [\<probing>](./file-schema/runtime/probing-element.md) elemento no arquivo de configuração de aplicativo para especificar subdiretórios que o tempo de execução deve pesquisar ao localizar um assembly.</span><span class="sxs-lookup"><span data-stu-id="eab27-120">You can use the [\<probing>](./file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="eab27-121">O exemplo a seguir mostra como especificar diretórios que o tempo de execução deve pesquisar.</span><span class="sxs-lookup"><span data-stu-id="eab27-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="eab27-122">O atributo **privatePath** contém os diretórios em que o tempo de execução deve pesquisar assemblies.</span><span class="sxs-lookup"><span data-stu-id="eab27-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="eab27-123">Se o aplicativo estiver localizado em C:\Program MyApp, o tempo de execução procurará assemblies que não especificam uma base de código em C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin e C:\Program Files\MyApp\Bin3.</span><span class="sxs-lookup"><span data-stu-id="eab27-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="eab27-124">Os diretórios especificados em **privatePath** devem ser subdiretórios do diretório base do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eab27-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eab27-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="eab27-125">See also</span></span>

- [<span data-ttu-id="eab27-126">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="eab27-126">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="eab27-127">Programação com assemblies</span><span class="sxs-lookup"><span data-stu-id="eab27-127">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="eab27-128">Como o runtime localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="eab27-128">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="eab27-129">Configurando aplicativos usando arquivos de configuração </span><span class="sxs-lookup"><span data-stu-id="eab27-129">Configuring Apps by using Configuration Files</span></span>](index.md)
