---
title: 'Como: Criar um par de chaves pública-privada'
ms.date: 08/20/2019
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
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 62c38494e29541bd490d69ccc8de485217b9514a
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991697"
---
# <a name="how-to-create-a-public-private-key-pair"></a><span data-ttu-id="b40c1-102">Como: Criar um par de chaves pública-privada</span><span class="sxs-lookup"><span data-stu-id="b40c1-102">How to: Create a public-private key pair</span></span>

<span data-ttu-id="b40c1-103">Para assinar um assembly com um nome forte, você deve ter um par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="b40c1-103">To sign an assembly with a strong name, you must have a public/private key pair.</span></span> <span data-ttu-id="b40c1-104">Esse par de chaves de criptografia pública/privada é usado durante a compilação para criar um assembly de nome forte.</span><span class="sxs-lookup"><span data-stu-id="b40c1-104">This public and private cryptographic key pair is used during compilation to create a strong-named assembly.</span></span> <span data-ttu-id="b40c1-105">Você pode criar um par de chaves usando a [ferramenta de Nome Forte (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="b40c1-105">You can create a key pair using the [Strong Name tool (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span> <span data-ttu-id="b40c1-106">Os arquivos do par de chaves geralmente têm uma extensão *. SNK* .</span><span class="sxs-lookup"><span data-stu-id="b40c1-106">Key pair files usually have an *.snk* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="b40c1-107">No Visual Studio, as C# páginas de propriedades do projeto e do Visual Basic incluem uma guia **assinatura** que permite selecionar arquivos de chave existentes ou gerar novos arquivos de chave sem usar o *sn. exe*.</span><span class="sxs-lookup"><span data-stu-id="b40c1-107">In Visual Studio, the C# and Visual Basic project property pages include a **Signing** tab that enables you to select existing key files or to generate new key files without using *Sn.exe*.</span></span> <span data-ttu-id="b40c1-108">No Visual C++, você pode especificar o local de um arquivo de chave existente na página de propriedades **Avançado** na seção **Vinculador** da seção **Propriedades de Configuração** da janela **Páginas de Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="b40c1-108">In Visual C++, you can specify the location of an existing key file in the **Advanced** property page in the **Linker** section of the **Configuration Properties** section of the **Property Pages** window.</span></span> <span data-ttu-id="b40c1-109">O uso do <xref:System.Reflection.AssemblyKeyFileAttribute> atributo para identificar pares de arquivos de chave tornou-se obsoleto a partir do Visual Studio 2005.</span><span class="sxs-lookup"><span data-stu-id="b40c1-109">The use of the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute to identify key file pairs was made obsolete beginning with Visual Studio 2005.</span></span>

## <a name="create-a-key-pair"></a><span data-ttu-id="b40c1-110">Criar um par de chaves</span><span class="sxs-lookup"><span data-stu-id="b40c1-110">Create a key pair</span></span>

<span data-ttu-id="b40c1-111">Para criar um par de chaves, em um prompt de comando, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="b40c1-111">To create a key pair, at a command prompt, type the following command:</span></span>

<span data-ttu-id="b40c1-112">**sn –k** \<*nome de arquivo*></span><span class="sxs-lookup"><span data-stu-id="b40c1-112">**sn –k** \<*file name*></span></span>

<span data-ttu-id="b40c1-113">Neste comando, *nome de arquivo* é o nome do arquivo de saída que contém o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="b40c1-113">In this command, *file name* is the name of the output file containing the key pair.</span></span>

<span data-ttu-id="b40c1-114">O exemplo a seguir cria um par de chaves chamado *sgKey. SNK*.</span><span class="sxs-lookup"><span data-stu-id="b40c1-114">The following example creates a key pair called *sgKey.snk*.</span></span>

```cmd
sn -k sgKey.snk
```

<span data-ttu-id="b40c1-115">Se você pretende atrasar a assinatura de um assembly e controla o par de chaves todo (o que é improvável fora de cenários de teste), pode usar os seguintes comandos para gerar um par de chaves e, em seguida, extrair a chave pública dele em um arquivo separado.</span><span class="sxs-lookup"><span data-stu-id="b40c1-115">If you intend to delay sign an assembly and you control the whole key pair (which is unlikely outside test scenarios), you can use the following commands to generate a key pair and then extract the public key from it into a separate file.</span></span> <span data-ttu-id="b40c1-116">Primeiro, crie o par de chaves:</span><span class="sxs-lookup"><span data-stu-id="b40c1-116">First, create the key pair:</span></span>

```cmd
sn -k keypair.snk
```

<span data-ttu-id="b40c1-117">Em seguida, extraia a chave pública do par de chaves e copie-a para um arquivo separado:</span><span class="sxs-lookup"><span data-stu-id="b40c1-117">Next, extract the public key from the key pair and copy it to a separate file:</span></span>

```cmd
sn -p keypair.snk public.snk
```

<span data-ttu-id="b40c1-118">Depois de criar o par de chaves, você deve colocar o arquivo onde as ferramentas de assinatura de nome forte possam encontrá-lo.</span><span class="sxs-lookup"><span data-stu-id="b40c1-118">Once you create the key pair, you must put the file where the strong name signing tools can find it.</span></span>

<span data-ttu-id="b40c1-119">Ao assinar um assembly com um nome forte, o [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) procura o arquivo de chave relativo ao diretório atual e ao diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="b40c1-119">When signing an assembly with a strong name, the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) looks for the key file relative to the current directory and to the output directory.</span></span> <span data-ttu-id="b40c1-120">Ao usar compiladores de linha de comando, você pode simplesmente copiar a chave para o diretório atual que contém seus módulos de código.</span><span class="sxs-lookup"><span data-stu-id="b40c1-120">When using command-line compilers, you can simply copy the key to the current directory containing your code modules.</span></span>

<span data-ttu-id="b40c1-121">Se você estiver usando uma versão anterior do Visual Studio que não tenha uma guia **Assinatura** nas propriedades do projeto, o local do arquivo de chave recomendado será o diretório do projeto com o atributo de arquivo especificado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b40c1-121">If you are using an earlier version of Visual Studio that does not have a **Signing** tab in the project properties, the recommended key file location is the project directory with the file attribute specified as follows:</span></span>

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

## <a name="see-also"></a><span data-ttu-id="b40c1-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b40c1-122">See also</span></span>

- [<span data-ttu-id="b40c1-123">Criar e usar assemblies de nome forte</span><span class="sxs-lookup"><span data-stu-id="b40c1-123">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
