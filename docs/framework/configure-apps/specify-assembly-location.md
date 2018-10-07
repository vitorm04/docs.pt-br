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
ms.openlocfilehash: 8fedec60b6152e77d6f99bf55cf11ec909fa8f80
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2018
ms.locfileid: "48848043"
---
# <a name="specifying-an-assembly39s-location"></a><span data-ttu-id="58bfb-102">Especificando um Assembly&#39;s local</span><span class="sxs-lookup"><span data-stu-id="58bfb-102">Specifying an Assembly&#39;s Location</span></span>
<span data-ttu-id="58bfb-103">Há duas maneiras para especificar o local de um assembly:</span><span class="sxs-lookup"><span data-stu-id="58bfb-103">There are two ways to specify an assembly's location:</span></span>  
  
-   <span data-ttu-id="58bfb-104">Usando o [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="58bfb-104">Using the [\<codeBase>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element.</span></span>  
  
-   <span data-ttu-id="58bfb-105">Usando o [ \<probing >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="58bfb-105">Using the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="58bfb-106">Você também pode usar o [.NET Framework Configuration Tool (Mscorcfg. msc)](https://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764) para especificar locais de assembly ou especificar locais para o common language runtime investigar assemblies.</span><span class="sxs-lookup"><span data-stu-id="58bfb-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](https://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="58bfb-107">Usando o \<codeBase > elemento</span><span class="sxs-lookup"><span data-stu-id="58bfb-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="58bfb-108">Você pode usar o  **\<codeBase >** elemento apenas na máquina configuração ou publicador arquivos de política que também redirecionar a versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="58bfb-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="58bfb-109">Quando o tempo de execução determina qual versão de assembly a ser usada, ela se aplica a configuração de base de código do arquivo que determina a versão.</span><span class="sxs-lookup"><span data-stu-id="58bfb-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="58bfb-110">Se nenhuma base de código estiver indicado, o tempo de execução investiga o assembly da maneira normal.</span><span class="sxs-lookup"><span data-stu-id="58bfb-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="58bfb-111">Para obter detalhes, consulte [como o tempo de execução Localiza Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="58bfb-111">For details, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="58bfb-112">O exemplo a seguir mostra como especificar o local de um assembly.</span><span class="sxs-lookup"><span data-stu-id="58bfb-112">The following example shows how to specify an assembly's location.</span></span>  
  
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
  
 <span data-ttu-id="58bfb-113">O **versão** atributo é necessário para todos os assemblies de nome forte, mas deve ser omitido para assemblies que não são forte.</span><span class="sxs-lookup"><span data-stu-id="58bfb-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="58bfb-114">O  **\<codeBase >** elemento requer o **href** atributo.</span><span class="sxs-lookup"><span data-stu-id="58bfb-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="58bfb-115">Não é possível especificar intervalos de versão na  **\<codeBase >** elemento.</span><span class="sxs-lookup"><span data-stu-id="58bfb-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58bfb-116">Se você estiver fornecendo uma referência de base de código para um assembly que não é forte, a dica deve apontar para a base do aplicativo ou em um subdiretório do diretório base do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="58bfb-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="58bfb-117">Usando o \<probing > elemento</span><span class="sxs-lookup"><span data-stu-id="58bfb-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="58bfb-118">O tempo de execução localiza assemblies que não têm uma base de código por sondagem.</span><span class="sxs-lookup"><span data-stu-id="58bfb-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="58bfb-119">Para obter mais informações sobre a investigação, consulte [como o tempo de execução Localiza Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="58bfb-119">For more information about probing, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="58bfb-120">Você pode usar o [ \<probing >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elemento no arquivo de configuração de aplicativo para especificar o tempo de execução deve pesquisar para localizar um assembly de subdiretórios.</span><span class="sxs-lookup"><span data-stu-id="58bfb-120">You can use the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="58bfb-121">O exemplo a seguir mostra como especificar diretórios de que tempo de execução deve pesquisar.</span><span class="sxs-lookup"><span data-stu-id="58bfb-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="58bfb-122">O **privatePath** atributo contém os diretórios que o tempo de execução deve procurar assemblies.</span><span class="sxs-lookup"><span data-stu-id="58bfb-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="58bfb-123">Se o aplicativo está localizado em C:\Program MyApp, o tempo de execução procura assemblies que não especificam uma base de código em C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin e C:\Program Files\MyApp\Bin3.</span><span class="sxs-lookup"><span data-stu-id="58bfb-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="58bfb-124">Diretórios especificados em **privatePath** devem ser subdiretórios do diretório base do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="58bfb-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58bfb-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58bfb-125">See Also</span></span>  
 [<span data-ttu-id="58bfb-126">Assemblies no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="58bfb-126">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [<span data-ttu-id="58bfb-127">Programação com assemblies</span><span class="sxs-lookup"><span data-stu-id="58bfb-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="58bfb-128">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="58bfb-128">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="58bfb-129">Configuração de aplicativos .NET Framework</span><span class="sxs-lookup"><span data-stu-id="58bfb-129">Configuring .NET Framework Apps</span></span>](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
