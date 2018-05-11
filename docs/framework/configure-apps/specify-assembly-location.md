---
title: Especificando um Assembly&#39;s local
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 65bd075115e33486e86e8081b01b96db665e9da5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="specifying-an-assembly39s-location"></a><span data-ttu-id="adff4-102">Especificando um Assembly&#39;s local</span><span class="sxs-lookup"><span data-stu-id="adff4-102">Specifying an Assembly&#39;s Location</span></span>
<span data-ttu-id="adff4-103">Há duas maneiras de especificar o local de um assembly:</span><span class="sxs-lookup"><span data-stu-id="adff4-103">There are two ways to specify an assembly's location:</span></span>  
  
-   <span data-ttu-id="adff4-104">Usando o [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="adff4-104">Using the [\<codeBase>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element.</span></span>  
  
-   <span data-ttu-id="adff4-105">Usando o [ \<probing >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="adff4-105">Using the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="adff4-106">Você também pode usar o [ferramenta de configuração do .NET Framework (Mscorcfg.msc)](http://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764) para especificar locais de assembly ou especificar locais para o common language runtime para investigação para assemblies.</span><span class="sxs-lookup"><span data-stu-id="adff4-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](http://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="adff4-107">Usando o \<codeBase > elemento</span><span class="sxs-lookup"><span data-stu-id="adff4-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="adff4-108">Você pode usar o  **\<codeBase >** elemento apenas na configuração ou publicador política arquivos de máquina que redirecionam também a versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="adff4-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="adff4-109">Quando o tempo de execução determina qual versão do assembly a ser usado, ele se aplica a configuração de base de código do arquivo que determina a versão.</span><span class="sxs-lookup"><span data-stu-id="adff4-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="adff4-110">Se nenhuma base de código é indicado, o tempo de execução de testes para o assembly da maneira normal.</span><span class="sxs-lookup"><span data-stu-id="adff4-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="adff4-111">Para obter detalhes, consulte [como o tempo de execução Localiza Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="adff4-111">For details, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="adff4-112">O exemplo a seguir mostra como especificar o local de um assembly.</span><span class="sxs-lookup"><span data-stu-id="adff4-112">The following example shows how to specify an assembly's location.</span></span>  
  
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
  
 <span data-ttu-id="adff4-113">O **versão** atributo é necessário para todos os assemblies de nomes fortes, mas devem ser omitido para assemblies que não são fortes.</span><span class="sxs-lookup"><span data-stu-id="adff4-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="adff4-114">O  **\<codeBase >** elemento requer o **href** atributo.</span><span class="sxs-lookup"><span data-stu-id="adff4-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="adff4-115">Você não pode especificar intervalos de versão no  **\<codeBase >** elemento.</span><span class="sxs-lookup"><span data-stu-id="adff4-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="adff4-116">Se você está fornecendo uma referência de base de código para um assembly que não está com nome forte, a dica deve apontar para a base de dados de aplicativo ou em um subdiretório do diretório base do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="adff4-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="adff4-117">Usando o \<probing > elemento</span><span class="sxs-lookup"><span data-stu-id="adff4-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="adff4-118">O tempo de execução localiza assemblies que não tem uma base de código por sondagem.</span><span class="sxs-lookup"><span data-stu-id="adff4-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="adff4-119">Para obter mais informações sobre a sondagem, consulte [como o tempo de execução Localiza Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="adff4-119">For more information about probing, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="adff4-120">Você pode usar o [ \<probing >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elemento no arquivo de configuração do aplicativo para especificar o tempo de execução deve pesquisar para localizar um assembly de subdiretórios.</span><span class="sxs-lookup"><span data-stu-id="adff4-120">You can use the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="adff4-121">O exemplo a seguir mostra como especificar diretórios que deve pesquisar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="adff4-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="adff4-122">O **privatePath** atributo contém os diretórios que o tempo de execução deve procurar por assemblies.</span><span class="sxs-lookup"><span data-stu-id="adff4-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="adff4-123">Se o aplicativo está localizado em MyApp C:\Program, o tempo de execução procurará assemblies que não especificam uma base de código em C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin e C:\Program Files\MyApp\Bin3.</span><span class="sxs-lookup"><span data-stu-id="adff4-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="adff4-124">Diretórios especificados em **privatePath** devem ser subdiretórios do diretório base do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="adff4-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adff4-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="adff4-125">See Also</span></span>  
 [<span data-ttu-id="adff4-126">Assemblies no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="adff4-126">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [<span data-ttu-id="adff4-127">Programação com assemblies</span><span class="sxs-lookup"><span data-stu-id="adff4-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="adff4-128">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="adff4-128">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="adff4-129">Configuração de aplicativos .NET Framework</span><span class="sxs-lookup"><span data-stu-id="adff4-129">Configuring .NET Framework Apps</span></span>](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
