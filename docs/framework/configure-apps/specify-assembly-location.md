---
title: Especificando o local de um assembly
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: ead69d1e850050214c15295134c06ff6f66e9760
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646026"
---
# <a name="specifying-an-assemblys-location"></a><span data-ttu-id="da1c3-102">Especificando o local de um assembly</span><span class="sxs-lookup"><span data-stu-id="da1c3-102">Specifying an Assembly's Location</span></span>
<span data-ttu-id="da1c3-103">Existem duas maneiras de especificar a localização de uma montagem:</span><span class="sxs-lookup"><span data-stu-id="da1c3-103">There are two ways to specify an assembly's location:</span></span>  
  
- <span data-ttu-id="da1c3-104">Usando [ \<](./file-schema/runtime/codebase-element.md) o elemento codeBase>.</span><span class="sxs-lookup"><span data-stu-id="da1c3-104">Using the [\<codeBase>](./file-schema/runtime/codebase-element.md) element.</span></span>  
  
- <span data-ttu-id="da1c3-105">Usando [ \<](./file-schema/runtime/probing-element.md) o elemento>sondagem.</span><span class="sxs-lookup"><span data-stu-id="da1c3-105">Using the [\<probing>](./file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="da1c3-106">Você também pode usar a [Ferramenta de Configuração do Framework .NET (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) para especificar locais de montagem ou especificar locais para o tempo de execução do idioma comum para sondar para conjuntos.</span><span class="sxs-lookup"><span data-stu-id="da1c3-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="da1c3-107">Usando \<o elemento codeBase></span><span class="sxs-lookup"><span data-stu-id="da1c3-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="da1c3-108">Você pode \*\* \<\*\* usar o elemento codeBase>apenas em arquivos de configuração de máquina ou diretiva de editor que também redirecionam a versão de montagem.</span><span class="sxs-lookup"><span data-stu-id="da1c3-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="da1c3-109">Quando o tempo de execução determina qual versão de montagem deve ser usada, ele aplica a configuração base de código do arquivo que determina a versão.</span><span class="sxs-lookup"><span data-stu-id="da1c3-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="da1c3-110">Se nenhuma base de código for indicada, os testes de tempo de execução para a montagem da maneira normal.</span><span class="sxs-lookup"><span data-stu-id="da1c3-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="da1c3-111">Para obter detalhes, [consulte Como o Runtime localiza montagens](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="da1c3-111">For details, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="da1c3-112">O exemplo a seguir mostra como especificar a localização de um conjunto.</span><span class="sxs-lookup"><span data-stu-id="da1c3-112">The following example shows how to specify an assembly's location.</span></span>  
  
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
  
 <span data-ttu-id="da1c3-113">O atributo de **versão** é necessário para todos os conjuntos com nome forte, mas deve ser omitido para conjuntos que não são fortes.</span><span class="sxs-lookup"><span data-stu-id="da1c3-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="da1c3-114">O \*\* \<\*\* elemento codeBase>requer o atributo **href.**</span><span class="sxs-lookup"><span data-stu-id="da1c3-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="da1c3-115">Não é possível especificar \*\* \<\*\* faixas de versão no elemento codeBase>.</span><span class="sxs-lookup"><span data-stu-id="da1c3-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="da1c3-116">Se você estiver fornecendo uma dica de base de código para um conjunto que não tenha um nome forte, a dica deve apontar para a base de aplicativos ou um subdiretório do diretório base de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="da1c3-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="da1c3-117">Usando \<o elemento> sondagem</span><span class="sxs-lookup"><span data-stu-id="da1c3-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="da1c3-118">O tempo de execução localiza conjuntos que não possuem uma base de código por sondagem.</span><span class="sxs-lookup"><span data-stu-id="da1c3-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="da1c3-119">Para obter mais informações sobre a sondagem, consulte [Como o Runtime Localiza Montagens](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="da1c3-119">For more information about probing, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="da1c3-120">Você pode [ \<](./file-schema/runtime/probing-element.md) usar o elemento de>de sondagem no arquivo de configuração do aplicativo para especificar subdiretórios que o tempo de execução deve pesquisar ao localizar um conjunto.</span><span class="sxs-lookup"><span data-stu-id="da1c3-120">You can use the [\<probing>](./file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="da1c3-121">O exemplo a seguir mostra como especificar diretórios que o tempo de execução deve ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="da1c3-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="da1c3-122">O atributo **privatePath** contém os diretórios que o tempo de execução deve procurar montagens.</span><span class="sxs-lookup"><span data-stu-id="da1c3-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="da1c3-123">Se o aplicativo estiver localizado em C:\Program Files\MyApp, o tempo de execução procurará conjuntos que não especifiquem uma base de código em C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin e C:\Program Files\MyApp\Bin3.</span><span class="sxs-lookup"><span data-stu-id="da1c3-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="da1c3-124">Os diretórios especificados no **privatePath** devem ser subdiretórios do diretório base de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="da1c3-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da1c3-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="da1c3-125">See also</span></span>

- [<span data-ttu-id="da1c3-126">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="da1c3-126">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="da1c3-127">Programação com assemblies</span><span class="sxs-lookup"><span data-stu-id="da1c3-127">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="da1c3-128">Como o runtime localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="da1c3-128">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="da1c3-129">Configurando aplicativos usando arquivos de configuração </span><span class="sxs-lookup"><span data-stu-id="da1c3-129">Configuring Apps by using Configuration Files</span></span>](index.md)
