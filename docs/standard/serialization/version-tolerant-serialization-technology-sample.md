---
title: Exemplo de tecnologia de serialização básica tolerante a versões
ms.date: 03/30/2017
ms.assetid: 2a183664-bfbf-4ff0-96f6-c836284ea916
ms.openlocfilehash: 317a47d46b839417e01eed9deca2459a96aaa201
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960774"
---
# <a name="version-tolerant-serialization-technology-sample"></a><span data-ttu-id="676f2-102">Exemplo de tecnologia de serialização básica tolerante a versões</span><span class="sxs-lookup"><span data-stu-id="676f2-102">Version Tolerant Serialization Technology Sample</span></span>
[<span data-ttu-id="676f2-103">Baixar Exemplo</span><span class="sxs-lookup"><span data-stu-id="676f2-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/VTS.zip.exe)  
  
 <span data-ttu-id="676f2-104">Esse exemplo demonstra os recursos de tolerância de versão da Serialização .NET.</span><span class="sxs-lookup"><span data-stu-id="676f2-104">This sample demonstrates the version tolerance features of .NET Serialization.</span></span> <span data-ttu-id="676f2-105">O exemplo cria aplicativos que usam versões diferentes de um <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> para serializar e desserializar dados.</span><span class="sxs-lookup"><span data-stu-id="676f2-105">The sample builds applications that use different versions of a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> to serialize and deserialize data.</span></span> <span data-ttu-id="676f2-106">Apesar da presença de diferentes versões de tipo, os aplicativos se comunicam de maneira simplificada.</span><span class="sxs-lookup"><span data-stu-id="676f2-106">Despite the presence of different type versions, the applications communicate seamlessly.</span></span> <span data-ttu-id="676f2-107">Para obter mais informações, consulte [Serialização tolerante a versão](../../../docs/standard/serialization/version-tolerant-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="676f2-107">For more information, see [Version Tolerant Serialization](../../../docs/standard/serialization/version-tolerant-serialization.md).</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="676f2-108">Para criar o exemplo usando o prompt de comando</span><span class="sxs-lookup"><span data-stu-id="676f2-108">To build the sample using the command prompt</span></span>  
  
1. <span data-ttu-id="676f2-109">Abra uma janela do Prompt de Comando e navegue para um dos subdiretórios específicos da linguagem (em V1 Application ou V2 Application) para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="676f2-109">Open a Command Prompt window and navigate to one of the language-specific subdirectories (under V1 Application or V2 Application) for the sample.</span></span>  
  
2. <span data-ttu-id="676f2-110">Digite **msbuild.exe \<ver> application.sln** na linha de comando (em que \<ver> é v1 ou v2).</span><span class="sxs-lookup"><span data-stu-id="676f2-110">Type **msbuild.exe \<ver> application.sln** at the command line (where \<ver> is either v1 or v2).</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="676f2-111">Para criar o exemplo usando Visual Studio</span><span class="sxs-lookup"><span data-stu-id="676f2-111">To build the sample using Visual Studio</span></span>  
  
1. <span data-ttu-id="676f2-112">Abra o explorador de arquivos e navegue até um dos subdiretórios específicos do idioma para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="676f2-112">Open File Explorer and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2. <span data-ttu-id="676f2-113">Navegue para o subdiretório V1 Application do diretório que você selecionou na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="676f2-113">Navigate to the V1 Application subdirectory of the directory you selected in the previous step.</span></span>  
  
3. <span data-ttu-id="676f2-114">Clique duas vezes no ícone para V1 Application.sln para abrir o arquivo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="676f2-114">Double-click the icon for V1 Application.sln to open the file in Visual Studio.</span></span>  
  
4. <span data-ttu-id="676f2-115">No menu **Compilar**, clique em **Compilar Solução**.</span><span class="sxs-lookup"><span data-stu-id="676f2-115">On the **Build** menu, click **Build Solution**.</span></span>  
  
5. <span data-ttu-id="676f2-116">Navegue para o subdiretório V2 Application e repita as duas etapas anteriores para criar o V2 Application.</span><span class="sxs-lookup"><span data-stu-id="676f2-116">Navigate to the V2 Application subdirectory and repeat the two previous steps to build the V2 Application.</span></span>  
  
 <span data-ttu-id="676f2-117">Os aplicativos serão criados nos subdiretórios padrão \bin ou \bin\Debug de seus respectivos diretórios de projeto.</span><span class="sxs-lookup"><span data-stu-id="676f2-117">The applications will be built in the default \bin or \bin\Debug subdirectories of their respective project directories.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="676f2-118">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="676f2-118">To run the sample</span></span>  
  
1. <span data-ttu-id="676f2-119">Na uma janela do Prompt de Comando, navegue para o subdiretório específico da linguagem que você selecionou ao criar os aplicativos de exemplo.</span><span class="sxs-lookup"><span data-stu-id="676f2-119">In the Command Prompt window, navigate to the language-specific subdirectory that you selected when you built the sample applications.</span></span>  
  
2. <span data-ttu-id="676f2-120">Digite **runme.cmd** na linha de comando para executar ambos os aplicativos de uma vez.</span><span class="sxs-lookup"><span data-stu-id="676f2-120">Type **runme.cmd** at the command line to run both applications at once.</span></span>  
  
 <span data-ttu-id="676f2-121">Como alternativa, navegue para os diretórios que contêm os novos executáveis e execute-os sequencialmente.</span><span class="sxs-lookup"><span data-stu-id="676f2-121">Alternatively, navigate to the directories that contain the new executables and run them sequentially.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="676f2-122">O exemplo cria aplicativos de console.</span><span class="sxs-lookup"><span data-stu-id="676f2-122">The sample builds console applications.</span></span> <span data-ttu-id="676f2-123">Você deve lançá-los e executá-los em uma janela do prompt de comando para exibir sua saída.</span><span class="sxs-lookup"><span data-stu-id="676f2-123">You must launch and run them in a Command Prompt window to view their output.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="676f2-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="676f2-124">See also</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.IO.FileStream>
