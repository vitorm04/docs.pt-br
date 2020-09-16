---
title: Arquivos mapeados na memória
description: Explore os arquivos mapeados na memória no .NET, que contêm o conteúdo do arquivo na memória virtual, e permita que os aplicativos modifiquem o arquivo gravando diretamente na memória.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- memory-mapped files
- inter-process communication
ms.assetid: a483d1b5-64aa-45b6-86ef-11b859f7f02e
ms.openlocfilehash: 74d821aff8308618f7c0efeb1b453db8214b877e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555940"
---
# <a name="memory-mapped-files"></a><span data-ttu-id="8ecfe-103">Arquivos mapeados na memória</span><span class="sxs-lookup"><span data-stu-id="8ecfe-103">Memory-Mapped Files</span></span>
<span data-ttu-id="8ecfe-104">Um arquivo mapeado pela memória tem o conteúdo de um arquivo em memória virtual.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-104">A memory-mapped file contains the contents of a file in virtual memory.</span></span> <span data-ttu-id="8ecfe-105">Esse mapeamento entre um espaço de arquivo e a memória permite que um aplicativo, inclusive vários processos, modifique o arquivo ao ler e gravar diretamente na memória.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-105">This mapping between a file and memory space enables an application, including multiple processes, to modify the file by reading and writing directly to the memory.</span></span> <span data-ttu-id="8ecfe-106">A partir do .NET Framework 4, é possível usar o código gerenciado para acessar arquivos mapeados na memória da mesma maneira que funções nativas do Windows acessam arquivos mapeados na memória, conforme descrito em [Gerenciamento de arquivos mapeados na memória](/previous-versions/ms810613(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="8ecfe-106">Starting with the .NET Framework 4, you can use managed code to access memory-mapped files in the same way that native Windows functions access memory-mapped files, as described in [Managing Memory-Mapped Files](/previous-versions/ms810613(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="8ecfe-107">Há dois tipos de arquivos mapeados na memória:</span><span class="sxs-lookup"><span data-stu-id="8ecfe-107">There are two types of memory-mapped files:</span></span>  
  
- <span data-ttu-id="8ecfe-108">Arquivos persistentes mapeados na memória</span><span class="sxs-lookup"><span data-stu-id="8ecfe-108">Persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="8ecfe-109">Arquivos persistentes são arquivos mapeados na memória associados a um arquivo de origem em um disco.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-109">Persisted files are memory-mapped files that are associated with a source file on a disk.</span></span> <span data-ttu-id="8ecfe-110">Quando o último processo termina de trabalhar com o arquivo, os dados são salvos no arquivo de origem no disco.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-110">When the last process has finished working with the file, the data is saved to the source file on the disk.</span></span> <span data-ttu-id="8ecfe-111">Esses arquivos mapeados na memória são adequados para trabalhar com arquivos de origem muito grandes.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-111">These memory-mapped files are suitable for working with extremely large source files.</span></span>  
  
- <span data-ttu-id="8ecfe-112">Arquivos não persistentes mapeados na memória</span><span class="sxs-lookup"><span data-stu-id="8ecfe-112">Non-persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="8ecfe-113">Arquivos não persistentes são arquivos mapeados na memória não associados a um arquivo em disco.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-113">Non-persisted files are memory-mapped files that are not associated with a file on a disk.</span></span> <span data-ttu-id="8ecfe-114">Quando o último processo termina de trabalhar com o arquivo, os dados são perdidos e o arquivo é solicitado pela coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-114">When the last process has finished working with the file, the data is lost and the file is reclaimed by garbage collection.</span></span> <span data-ttu-id="8ecfe-115">Esses arquivos são adequados para a criação de memória compartilhada para comunicações entre processos (IPC).</span><span class="sxs-lookup"><span data-stu-id="8ecfe-115">These files are suitable for creating shared memory for inter-process communications (IPC).</span></span>  
  
## <a name="processes-views-and-managing-memory"></a><span data-ttu-id="8ecfe-116">Processos, exibição e gerenciamento de memória</span><span class="sxs-lookup"><span data-stu-id="8ecfe-116">Processes, Views, and Managing Memory</span></span>  
 <span data-ttu-id="8ecfe-117">Os arquivos mapeados na memória podem ser compartilhados entre vários processos.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-117">Memory-mapped files can be shared across multiple processes.</span></span> <span data-ttu-id="8ecfe-118">Os processos podem mapear para o mesmo arquivo mapeado na memória usando um nome comum, que é atribuído pelo processo que criou o arquivo.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-118">Processes can map to the same memory-mapped file by using a common name that is assigned by the process that created the file.</span></span>  
  
 <span data-ttu-id="8ecfe-119">Para trabalhar com um arquivo mapeado na memória, você deve criar uma exibição de todo o arquivo mapeado na memória ou de parte dele.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-119">To work with a memory-mapped file, you must create a view of the entire memory-mapped file or a part of it.</span></span> <span data-ttu-id="8ecfe-120">Também é possível criar vários modos de exibição para a mesma parte do arquivo mapeado na memória, criando assim memórias simultâneas.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-120">You can also create multiple views to the same part of the memory-mapped file, thereby creating concurrent memory.</span></span> <span data-ttu-id="8ecfe-121">Para que dois modos de exibição permaneçam simultâneos, precisam ser criados usando o mesmo arquivo de memória mapeada.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-121">For two views to remain concurrent, they have to be created from the same memory-mapped file.</span></span>  
  
 <span data-ttu-id="8ecfe-122">Vários modos de exibição também poderão ser necessários se o arquivo for maior que o tamanho do espaço de memória lógica do aplicativo disponível para o mapeamento de memória (2GB em um computador de 32 bits).</span><span class="sxs-lookup"><span data-stu-id="8ecfe-122">Multiple views may also be necessary if the file is greater than the size of the application’s logical memory space available for memory mapping (2 GB on a 32-bit computer).</span></span>  
  
 <span data-ttu-id="8ecfe-123">Há dois tipos de modos de exibição: modo de exibição de acesso por fluxo e modo de exibição de acesso aleatório.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-123">There are two types of views: stream access view and random access view.</span></span> <span data-ttu-id="8ecfe-124">Use os modos de exibição de acesso por fluxo para acessos sequenciais a um arquivo. Isso é recomendado para arquivos não persistentes e IPCs.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-124">Use stream access views for sequential access to a file; this is recommended for non-persisted files and IPC.</span></span> <span data-ttu-id="8ecfe-125">A preferência é para os modos de exibição de acessos aleatórios para trabalhos com arquivos persistentes.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-125">Random access views are preferred for working with persisted files.</span></span>  
  
 <span data-ttu-id="8ecfe-126">Os arquivos mapeados na memória são acessados pelo gerenciador de memória do sistema operacional, então o arquivo é automaticamente particionado em um número de páginas e acessado conforme a necessidade.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-126">Memory-mapped files are accessed through the operating system’s memory manager, so the file is automatically partitioned into a number of pages and accessed as needed.</span></span> <span data-ttu-id="8ecfe-127">Não é preciso lidar com o gerenciamento de memória por conta própria.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-127">You do not have to handle the memory management yourself.</span></span>  
  
 <span data-ttu-id="8ecfe-128">A ilustração a seguir mostra como vários processos podem ter modos de exibição variados e sobrepostos para o mesmo arquivo mapeado na memória ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-128">The following illustration shows how multiple processes can have multiple and overlapping views to the same memory-mapped file at the same time.</span></span>

 <span data-ttu-id="8ecfe-129">A seguinte imagem mostra várias exibições sobrepostas em um arquivo mapeado em memória:</span><span class="sxs-lookup"><span data-stu-id="8ecfe-129">The following image shows multiple and overlapped views to a memory-mapped file:</span></span>  
  
 ![Captura de tela que mostra as exibições em um arquivo mapeado em memória.](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a><span data-ttu-id="8ecfe-131">Programar com arquivos mapeados na memória</span><span class="sxs-lookup"><span data-stu-id="8ecfe-131">Programming with Memory-Mapped Files</span></span>  
 <span data-ttu-id="8ecfe-132">A tabela a seguir orienta como usar objetos de arquivos mapeados na memória e os membros deles.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-132">The following table provides a guide for using memory-mapped file objects and their members.</span></span>  
  
|<span data-ttu-id="8ecfe-133">Tarefa</span><span class="sxs-lookup"><span data-stu-id="8ecfe-133">Task</span></span>|<span data-ttu-id="8ecfe-134">Métodos ou propriedades a serem usados</span><span class="sxs-lookup"><span data-stu-id="8ecfe-134">Methods or properties to use</span></span>|  
|----------|----------------------------------|  
|<span data-ttu-id="8ecfe-135">Para obter um objeto <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> de um arquivo no disco que representa um arquivo persistente mapeado na memória.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-135">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a persisted memory-mapped file from a file on disk.</span></span>|<span data-ttu-id="8ecfe-136">Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-136"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="8ecfe-137">Para obter um objeto <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> que representa um arquivo não persistente mapeado na memória (não associado a um arquivo no disco).</span><span class="sxs-lookup"><span data-stu-id="8ecfe-137">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a non-persisted memory-mapped file (not associated with a file on disk).</span></span>|<span data-ttu-id="8ecfe-138">Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-138"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> method.</span></span><br /><br /> <span data-ttu-id="8ecfe-139">- ou -</span><span class="sxs-lookup"><span data-stu-id="8ecfe-139">- or -</span></span><br /><br /> <span data-ttu-id="8ecfe-140">Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-140"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="8ecfe-141">Para obter um objeto <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> de um arquivo mapeado na memória existente (persistente ou não persistente).</span><span class="sxs-lookup"><span data-stu-id="8ecfe-141">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object of an existing memory-mapped file (either persisted or non-persisted).</span></span>|<span data-ttu-id="8ecfe-142">Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-142"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="8ecfe-143">Para obter um objeto <xref:System.IO.UnmanagedMemoryStream> para uma exibição de acesso em sequência para o arquivo mapeado na memória.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-143">To obtain a <xref:System.IO.UnmanagedMemoryStream> object for a sequentially accessed view to the memory-mapped file.</span></span>|<span data-ttu-id="8ecfe-144">Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-144"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="8ecfe-145">Para obter um objeto <xref:System.IO.UnmanagedMemoryAccessor> para uma exibição de acesso aleatório para um arquivo mapeado na memória.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-145">To obtain a <xref:System.IO.UnmanagedMemoryAccessor> object for a random access view to a memory-mapped fie.</span></span>|<span data-ttu-id="8ecfe-146">Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-146"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="8ecfe-147">Para obter um objeto <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> a ser usado com um código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-147">To obtain a <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> object to use with unmanaged code.</span></span>|<span data-ttu-id="8ecfe-148">Propriedade <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-148"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="8ecfe-149">- ou -</span><span class="sxs-lookup"><span data-stu-id="8ecfe-149">- or -</span></span><br /><br /> <span data-ttu-id="8ecfe-150">Propriedade <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-150"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="8ecfe-151">- ou -</span><span class="sxs-lookup"><span data-stu-id="8ecfe-151">- or -</span></span><br /><br /> <span data-ttu-id="8ecfe-152">Propriedade <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-152"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span>|  
|<span data-ttu-id="8ecfe-153">Para atrasar a alocação de memória até que uma exibição seja criada (somente arquivos não persistentes).</span><span class="sxs-lookup"><span data-stu-id="8ecfe-153">To delay allocating memory until a view is created (non-persisted files only).</span></span><br /><br /> <span data-ttu-id="8ecfe-154">Para determinar o tamanho de página atual do sistema, use a propriedade <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-154">(To determine the current system page size, use the <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> property.)</span></span>|<span data-ttu-id="8ecfe-155">Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> com o valor <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-155"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> method with the <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> value.</span></span><br /><br /> <span data-ttu-id="8ecfe-156">- ou -</span><span class="sxs-lookup"><span data-stu-id="8ecfe-156">- or -</span></span><br /><br /> <span data-ttu-id="8ecfe-157">Métodos <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> que possuem uma enumeração <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> como parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-157"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods that have a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> enumeration as a parameter.</span></span>|  
  
### <a name="security"></a><span data-ttu-id="8ecfe-158">Segurança</span><span class="sxs-lookup"><span data-stu-id="8ecfe-158">Security</span></span>  
 <span data-ttu-id="8ecfe-159">É possível aplicar os direitos de acesso ao criar um arquivo mapeado na memória usando os seguintes métodos que usam uma enumeração <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> como parâmetro:</span><span class="sxs-lookup"><span data-stu-id="8ecfe-159">You can apply access rights when you create a memory-mapped file, by using the following methods that take a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> enumeration as a parameter:</span></span>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="8ecfe-160">É possível especificar os direitos de acesso para abrir um arquivo mapeado na memória existente usando os métodos <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> que usam <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> como parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-160">You can specify access rights for opening an existing memory-mapped file by using the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> methods that take an <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> as a parameter.</span></span>  
  
 <span data-ttu-id="8ecfe-161">Além disso, é possível incluir um objeto <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> que contém regras de acesso predefinidas.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-161">In addition, you can include a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> object that contains predefined access rules.</span></span>  
  
 <span data-ttu-id="8ecfe-162">Para aplicar as regras de acesso novas ou modificadas a um arquivo mapeado na memória, use o método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A>.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-162">To apply new or changed access rules to a memory-mapped file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> method.</span></span> <span data-ttu-id="8ecfe-163">Para recuperar as regras de acesso ou de auditoria de um arquivo existente, use o método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A>.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-163">To retrieve access or audit rules from an existing file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="8ecfe-164">Exemplos</span><span class="sxs-lookup"><span data-stu-id="8ecfe-164">Examples</span></span>  
  
### <a name="persisted-memory-mapped-files"></a><span data-ttu-id="8ecfe-165">Arquivos persistentes mapeados na memória</span><span class="sxs-lookup"><span data-stu-id="8ecfe-165">Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="8ecfe-166">Os métodos <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> criam um arquivo mapeado na memória de um arquivo existente no disco.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-166">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> methods create a memory-mapped file from an existing file on disk.</span></span>  
  
 <span data-ttu-id="8ecfe-167">O exemplo a seguir cria uma exibição de mapeamento na memória de parte de um arquivo muito grande e manipula uma porção dele.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-167">The following example creates a memory-mapped view of a part of an extremely large file and manipulates a portion of it.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

 <span data-ttu-id="8ecfe-168">O exemplo a seguir abre o mesmo arquivo mapeado na memória para outro processo.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-168">The following example opens the same memory-mapped file for another process.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a><span data-ttu-id="8ecfe-169">Arquivos não persistentes mapeados na memória</span><span class="sxs-lookup"><span data-stu-id="8ecfe-169">Non-Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="8ecfe-170">Os métodos <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> e <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> criam um arquivo mapeado na memória que não está mapeado para um arquivo existente no disco.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-170">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> and <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods create a memory-mapped file that is not mapped to an existing file on disk.</span></span>  
  
 <span data-ttu-id="8ecfe-171">O exemplo a seguir consiste de três processos separados (aplicativos de console) que gravam valores booleanos em um arquivo mapeado na memória.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-171">The following example consists of three separate processes (console applications) that write Boolean values to a memory-mapped file.</span></span> <span data-ttu-id="8ecfe-172">Ocorre a seguinte sequência de ações:</span><span class="sxs-lookup"><span data-stu-id="8ecfe-172">The following sequence of actions occur:</span></span>  
  
1. <span data-ttu-id="8ecfe-173">O `Process A` cria o arquivo mapeado na memória e grava um valor para ele.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-173">`Process A` creates the memory-mapped file and writes a value to it.</span></span>  
  
2. <span data-ttu-id="8ecfe-174">O `Process B` abre o arquivo mapeado na memória e grava um valor para ele.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-174">`Process B` opens the memory-mapped file and writes a value to it.</span></span>  
  
3. <span data-ttu-id="8ecfe-175">O `Process C` abre o arquivo mapeado na memória e grava um valor para ele.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-175">`Process C` opens the memory-mapped file and writes a value to it.</span></span>  
  
4. <span data-ttu-id="8ecfe-176">O `Process A` lê e exibe os valores do arquivo mapeado na memória.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-176">`Process A` reads and displays the values from the memory-mapped file.</span></span>  
  
5. <span data-ttu-id="8ecfe-177">Após o `Process A` concluir com o arquivo mapeado na memória, o arquivo é imediatamente recuperado pela coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-177">After `Process A` is finished with the memory-mapped file, the file is immediately reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="8ecfe-178">Para executar este exemplo, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8ecfe-178">To run this example, do the following:</span></span>  
  
1. <span data-ttu-id="8ecfe-179">Compile os aplicativos e abra três janelas de Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-179">Compile the applications and open three Command Prompt windows.</span></span>  
  
2. <span data-ttu-id="8ecfe-180">Na primeira janela do prompt, execute o `Process A`.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-180">In the first Command Prompt window, run `Process A`.</span></span>  
  
3. <span data-ttu-id="8ecfe-181">Na segunda janela, execute o `Process B`.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-181">In the second Command Prompt window, run `Process B`.</span></span>  
  
4. <span data-ttu-id="8ecfe-182">Retorne ao `Process A` e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-182">Return to `Process A` and press ENTER.</span></span>  
  
5. <span data-ttu-id="8ecfe-183">Na terceira janela do prompt, execute o `Process C`.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-183">In the third Command Prompt window, run `Process C`.</span></span>  
  
6. <span data-ttu-id="8ecfe-184">Retorne ao `Process A` e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="8ecfe-184">Return to `Process A` and press ENTER.</span></span>  
  
 <span data-ttu-id="8ecfe-185">A saída do `Process A` é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="8ecfe-185">The output of `Process A` is as follows:</span></span>  
  
```console  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 <span data-ttu-id="8ecfe-186">**Processo A**</span><span class="sxs-lookup"><span data-stu-id="8ecfe-186">**Process A**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 <span data-ttu-id="8ecfe-187">**Processo B**</span><span class="sxs-lookup"><span data-stu-id="8ecfe-187">**Process B**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 <span data-ttu-id="8ecfe-188">**Processo C**</span><span class="sxs-lookup"><span data-stu-id="8ecfe-188">**Process C**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8ecfe-189">Confira também</span><span class="sxs-lookup"><span data-stu-id="8ecfe-189">See also</span></span>

- [<span data-ttu-id="8ecfe-190">Arquivo e e/s de fluxo</span><span class="sxs-lookup"><span data-stu-id="8ecfe-190">File and Stream I/O</span></span>](index.md)
