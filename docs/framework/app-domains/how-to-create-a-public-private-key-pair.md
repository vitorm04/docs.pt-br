---
title: "Como criar um par de chaves pública/privada"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- key pairs for strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- cryptographic key pairs
- snk files (key pair files)
- public-private key pairs
- .snk files
- strong-named assemblies, key pairs
ms.assetid: 05026813-f3bd-4d7c-9e0b-fc588eb3d114
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a0d1f54b417a9752ae96e52f78d9df7d2d60cbec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-public-private-key-pair"></a><span data-ttu-id="971f8-102">Como criar um par de chaves pública/privada</span><span class="sxs-lookup"><span data-stu-id="971f8-102">How to: Create a Public-Private Key Pair</span></span>
<span data-ttu-id="971f8-103">Para assinar um assembly com um nome forte, você deve ter um par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="971f8-103">To sign an assembly with a strong name, you must have a public/private key pair.</span></span> <span data-ttu-id="971f8-104">Esse par de chaves de criptografia pública/privada é usado durante a compilação para criar um assembly de nome forte.</span><span class="sxs-lookup"><span data-stu-id="971f8-104">This public and private cryptographic key pair is used during compilation to create a strong-named assembly.</span></span> <span data-ttu-id="971f8-105">Você pode criar um par de chaves usando a [ferramenta de Nome Forte (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="971f8-105">You can create a key pair using the [Strong Name tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).</span></span> <span data-ttu-id="971f8-106">Os arquivos de par de chaves geralmente têm uma extensão .snk.</span><span class="sxs-lookup"><span data-stu-id="971f8-106">Key pair files usually have an .snk extension.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="971f8-107">No [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], as páginas de propriedades de projeto C# e Visual Basic incluem uma guia **Assinatura** que permite que você selecione arquivos de chave existentes ou gere novos arquivos de chaves sem usar Sn.exe.</span><span class="sxs-lookup"><span data-stu-id="971f8-107">In [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], the C# and Visual Basic project property pages include a **Signing** tab that enables you to select existing key files or to generate new key files without using Sn.exe.</span></span> <span data-ttu-id="971f8-108">No Visual C++, você pode especificar o local de um arquivo de chave existente na página de propriedades **Avançado** na seção **Vinculador** da seção **Propriedades de Configuração** da janela **Páginas de Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="971f8-108">In Visual C++, you can specify the location of an existing key file in the **Advanced** property page in the **Linker** section of the **Configuration Properties** section of the **Property Pages** window.</span></span> <span data-ttu-id="971f8-109">O uso do atributo <xref:System.Reflection.AssemblyKeyFileAttribute> para identificar pares de arquivos de chave se tornou obsoleto começando com [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="971f8-109">The use of the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute to identify key file pairs has been made obsolete beginning with [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)].</span></span>  
  
### <a name="to-create-a-key-pair"></a><span data-ttu-id="971f8-110">Para criar um par de chaves</span><span class="sxs-lookup"><span data-stu-id="971f8-110">To create a key pair</span></span>  
  
1.  <span data-ttu-id="971f8-111">No prompt de comando, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="971f8-111">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="971f8-112">**sn –k** \<*nome de arquivo*></span><span class="sxs-lookup"><span data-stu-id="971f8-112">**sn –k** \<*file name*></span></span>  
  
     <span data-ttu-id="971f8-113">Neste comando, *nome de arquivo* é o nome do arquivo de saída que contém o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="971f8-113">In this command, *file name* is the name of the output file containing the key pair.</span></span>  
  
 <span data-ttu-id="971f8-114">O exemplo a seguir cria um par de chaves chamado `sgKey.snk`.</span><span class="sxs-lookup"><span data-stu-id="971f8-114">The following example creates a key pair called `sgKey.snk`.</span></span>  
  
```  
sn -k sgKey.snk  
```  
  
 <span data-ttu-id="971f8-115">Se você pretende atrasar a assinatura de um assembly e controla o par de chaves todo (o que é improvável fora de cenários de teste), pode usar os seguintes comandos para gerar um par de chaves e, em seguida, extrair a chave pública dele em um arquivo separado.</span><span class="sxs-lookup"><span data-stu-id="971f8-115">If you intend to delay sign an assembly and you control the whole key pair (which is unlikely outside test scenarios), you can use the following commands to generate a key pair and then extract the public key from it into a separate file.</span></span> <span data-ttu-id="971f8-116">Primeiro, crie o par de chaves:</span><span class="sxs-lookup"><span data-stu-id="971f8-116">First, create the key pair:</span></span>  
  
```  
sn -k keypair.snk  
```  
  
 <span data-ttu-id="971f8-117">Em seguida, extraia a chave pública do par de chaves e copie-a para um arquivo separado:</span><span class="sxs-lookup"><span data-stu-id="971f8-117">Next, extract the public key from the key pair and copy it to a separate file:</span></span>  
  
```  
sn -p keypair.snk public.snk  
```  
  
 <span data-ttu-id="971f8-118">Depois de criar o par de chaves, você deve colocar o arquivo onde as ferramentas de assinatura de nome forte possam encontrá-lo.</span><span class="sxs-lookup"><span data-stu-id="971f8-118">Once you create the key pair, you must put the file where the strong name signing tools can find it.</span></span>  
  
 <span data-ttu-id="971f8-119">Ao assinar um assembly com um nome forte, o [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) procura o arquivo de chave relativo ao diretório atual e ao diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="971f8-119">When signing an assembly with a strong name, the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) looks for the key file relative to the current directory and to the output directory.</span></span> <span data-ttu-id="971f8-120">Ao usar compiladores de linha de comando, você pode simplesmente copiar a chave para o diretório atual que contém seus módulos de código.</span><span class="sxs-lookup"><span data-stu-id="971f8-120">When using command-line compilers, you can simply copy the key to the current directory containing your code modules.</span></span>  
  
 <span data-ttu-id="971f8-121">Se você estiver usando uma versão anterior do [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] que não tem uma guia **Assinatura** nas propriedades do projeto, o local do arquivo de chave recomendado é o diretório do projeto com o atributo de arquivo especificado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="971f8-121">If you are using an earlier version of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] that does not have a **Signing** tab in the project properties, the recommended key file location is the project directory with the file attribute specified as follows:</span></span>  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="971f8-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="971f8-122">See Also</span></span>  
 [<span data-ttu-id="971f8-123">Criar e usar assemblies de nomes fortes</span><span class="sxs-lookup"><span data-stu-id="971f8-123">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
