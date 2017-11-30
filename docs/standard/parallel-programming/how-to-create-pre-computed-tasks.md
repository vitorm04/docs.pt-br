---
title: "Como: Criar tarefas pré-computadas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4596b28afe48aad4a84a7dd72b4a1d44a9ada8a2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-pre-computed-tasks"></a><span data-ttu-id="0f5e9-102">Como: Criar tarefas pré-computadas</span><span class="sxs-lookup"><span data-stu-id="0f5e9-102">How to: Create Pre-Computed Tasks</span></span>
<span data-ttu-id="0f5e9-103">Este documento descreve como usar o <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> método para recuperar os resultados das operações assíncronas de download que são mantidos em um cache.</span><span class="sxs-lookup"><span data-stu-id="0f5e9-103">This document describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.</span></span> <span data-ttu-id="0f5e9-104">O <xref:System.Threading.Tasks.Task.FromResult%2A> método retorna um terminar <xref:System.Threading.Tasks.Task%601> objeto que contém o valor fornecido como sua <xref:System.Threading.Tasks.Task%601.Result%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="0f5e9-104">The <xref:System.Threading.Tasks.Task.FromResult%2A> method returns a finished <xref:System.Threading.Tasks.Task%601> object that holds the provided value as its <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="0f5e9-105">Este método é útil quando você executa uma operação assíncrona que retorna um objeto <xref:System.Threading.Tasks.Task%601> e o resultado do objeto <xref:System.Threading.Tasks.Task%601> já está calculado.</span><span class="sxs-lookup"><span data-stu-id="0f5e9-105">This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f5e9-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0f5e9-106">Example</span></span>  
 <span data-ttu-id="0f5e9-107">O exemplo a seguir faz o download de cadeias de caracteres da web.</span><span class="sxs-lookup"><span data-stu-id="0f5e9-107">The following example downloads strings from the web.</span></span> <span data-ttu-id="0f5e9-108">Define o `DownloadStringAsync` método.</span><span class="sxs-lookup"><span data-stu-id="0f5e9-108">It defines the `DownloadStringAsync` method.</span></span> <span data-ttu-id="0f5e9-109">Esse método baixa cadeias de caracteres da web assincronamente.</span><span class="sxs-lookup"><span data-stu-id="0f5e9-109">This method downloads strings from the web asynchronously.</span></span> <span data-ttu-id="0f5e9-110">Este exemplo também usa um <xref:System.Collections.Concurrent.ConcurrentDictionary%602> objeto em cache os resultados de operações anteriores.</span><span class="sxs-lookup"><span data-stu-id="0f5e9-110">This example also uses a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> object to cache the results of previous operations.</span></span> <span data-ttu-id="0f5e9-111">Se o endereço de entrada é mantido no cache, `DownloadStringAsync` usa o <xref:System.Threading.Tasks.Task.FromResult%2A> método para produzir um <xref:System.Threading.Tasks.Task%601> objeto que contém o conteúdo nesse endereço.</span><span class="sxs-lookup"><span data-stu-id="0f5e9-111">If the input address is held in this cache, `DownloadStringAsync` uses the <xref:System.Threading.Tasks.Task.FromResult%2A> method to produce a <xref:System.Threading.Tasks.Task%601> object that holds the content at that address.</span></span> <span data-ttu-id="0f5e9-112">Caso contrário, `DownloadStringAsync` baixa o arquivo da web e adiciona o resultado para o cache.</span><span class="sxs-lookup"><span data-stu-id="0f5e9-112">Otherwise, `DownloadStringAsync` downloads the file from the web and adds the result to the cache.</span></span>  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 <span data-ttu-id="0f5e9-113">Esse exemplo calcula o tempo necessário para baixar várias cadeias de caracteres duas vezes.</span><span class="sxs-lookup"><span data-stu-id="0f5e9-113">This example computes the time that is required to download multiple strings two times.</span></span> <span data-ttu-id="0f5e9-114">O segundo conjunto de operações de download deve levar menos tempo do que o primeiro conjunto porque os resultados são mantidos no cache.</span><span class="sxs-lookup"><span data-stu-id="0f5e9-114">The second set of download operations should take less time than the first set because the results are held in the cache.</span></span> <span data-ttu-id="0f5e9-115">O <xref:System.Threading.Tasks.Task.FromResult%2A> método habilita o `DownloadStringAsync` método para criar <xref:System.Threading.Tasks.Task%601> objetos que contêm esses pré-computadas resultados.</span><span class="sxs-lookup"><span data-stu-id="0f5e9-115">The <xref:System.Threading.Tasks.Task.FromResult%2A> method enables the `DownloadStringAsync` method to create <xref:System.Threading.Tasks.Task%601> objects that hold these pre-computed results.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0f5e9-116">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="0f5e9-116">Compiling the Code</span></span>  
 <span data-ttu-id="0f5e9-117">Copie o código de exemplo e cole-o em um projeto do Visual Studio ou colá-lo em um arquivo chamado `CachedDownloads.cs` (`CachedDownloads.vb` para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), e, em seguida, execute o seguinte comando em uma janela de Prompt de comando do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0f5e9-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `CachedDownloads.cs` (`CachedDownloads.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="0f5e9-118">**CSC.exe CachedDownloads.cs**</span><span class="sxs-lookup"><span data-stu-id="0f5e9-118">**csc.exe CachedDownloads.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="0f5e9-119">**Vbc.exe CachedDownloads.vb**</span><span class="sxs-lookup"><span data-stu-id="0f5e9-119">**vbc.exe CachedDownloads.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="0f5e9-120">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="0f5e9-120">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f5e9-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f5e9-121">See Also</span></span>  
 [<span data-ttu-id="0f5e9-122">Programação assíncrona baseada em tarefa</span><span class="sxs-lookup"><span data-stu-id="0f5e9-122">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
