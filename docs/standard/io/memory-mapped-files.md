---
title: Arquivos mapeados na memória
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- memory-mapped files
- inter-process communication
ms.assetid: a483d1b5-64aa-45b6-86ef-11b859f7f02e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f7bda02e1862740e6a6328835367a6a5e9929033
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59328303"
---
# <a name="memory-mapped-files"></a><span data-ttu-id="840b7-102">Arquivos mapeados na memória</span><span class="sxs-lookup"><span data-stu-id="840b7-102">Memory-Mapped Files</span></span>
<span data-ttu-id="840b7-103">Um arquivo mapeado pela memória tem o conteúdo de um arquivo em memória virtual.</span><span class="sxs-lookup"><span data-stu-id="840b7-103">A memory-mapped file contains the contents of a file in virtual memory.</span></span> <span data-ttu-id="840b7-104">Esse mapeamento entre um espaço de arquivo e a memória permite que um aplicativo, inclusive vários processos, modifique o arquivo ao ler e gravar diretamente na memória.</span><span class="sxs-lookup"><span data-stu-id="840b7-104">This mapping between a file and memory space enables an application, including multiple processes, to modify the file by reading and writing directly to the memory.</span></span> <span data-ttu-id="840b7-105">Começando com o [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], é possível usar o código gerenciado para acessar arquivos mapeados na memória da mesma maneira que funções nativas do Windows acessam arquivos mapeados na memória, conforme descrito em [Gerenciamento de arquivos mapeados na memória](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="840b7-105">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use managed code to access memory-mapped files in the same way that native Windows functions access memory-mapped files, as described in [Managing Memory-Mapped Files](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="840b7-106">Há dois tipos de arquivos mapeados na memória:</span><span class="sxs-lookup"><span data-stu-id="840b7-106">There are two types of memory-mapped files:</span></span>  
  
-   <span data-ttu-id="840b7-107">Arquivos persistentes mapeados na memória</span><span class="sxs-lookup"><span data-stu-id="840b7-107">Persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="840b7-108">Arquivos persistentes são arquivos mapeados na memória associados a um arquivo de origem em um disco.</span><span class="sxs-lookup"><span data-stu-id="840b7-108">Persisted files are memory-mapped files that are associated with a source file on a disk.</span></span> <span data-ttu-id="840b7-109">Quando o último processo termina de trabalhar com o arquivo, os dados são salvos no arquivo de origem no disco.</span><span class="sxs-lookup"><span data-stu-id="840b7-109">When the last process has finished working with the file, the data is saved to the source file on the disk.</span></span> <span data-ttu-id="840b7-110">Esses arquivos mapeados na memória são adequados para trabalhar com arquivos de origem muito grandes.</span><span class="sxs-lookup"><span data-stu-id="840b7-110">These memory-mapped files are suitable for working with extremely large source files.</span></span>  
  
-   <span data-ttu-id="840b7-111">Arquivos não persistentes mapeados na memória</span><span class="sxs-lookup"><span data-stu-id="840b7-111">Non-persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="840b7-112">Arquivos não persistentes são arquivos mapeados na memória não associados a um arquivo em disco.</span><span class="sxs-lookup"><span data-stu-id="840b7-112">Non-persisted files are memory-mapped files that are not associated with a file on a disk.</span></span> <span data-ttu-id="840b7-113">Quando o último processo termina de trabalhar com o arquivo, os dados são perdidos e o arquivo é solicitado pela coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="840b7-113">When the last process has finished working with the file, the data is lost and the file is reclaimed by garbage collection.</span></span> <span data-ttu-id="840b7-114">Esses arquivos são adequados para a criação de memória compartilhada para comunicações entre processos (IPC).</span><span class="sxs-lookup"><span data-stu-id="840b7-114">These files are suitable for creating shared memory for inter-process communications (IPC).</span></span>  
  
## <a name="processes-views-and-managing-memory"></a><span data-ttu-id="840b7-115">Processos, exibição e gerenciamento de memória</span><span class="sxs-lookup"><span data-stu-id="840b7-115">Processes, Views, and Managing Memory</span></span>  
 <span data-ttu-id="840b7-116">Os arquivos mapeados na memória podem ser compartilhados entre vários processos.</span><span class="sxs-lookup"><span data-stu-id="840b7-116">Memory-mapped files can be shared across multiple processes.</span></span> <span data-ttu-id="840b7-117">Os processos podem mapear para o mesmo arquivo mapeado na memória usando um nome comum, que é atribuído pelo processo que criou o arquivo.</span><span class="sxs-lookup"><span data-stu-id="840b7-117">Processes can map to the same memory-mapped file by using a common name that is assigned by the process that created the file.</span></span>  
  
 <span data-ttu-id="840b7-118">Para trabalhar com um arquivo mapeado na memória, você deve criar uma exibição de todo o arquivo mapeado na memória ou de parte dele.</span><span class="sxs-lookup"><span data-stu-id="840b7-118">To work with a memory-mapped file, you must create a view of the entire memory-mapped file or a part of it.</span></span> <span data-ttu-id="840b7-119">Também é possível criar vários modos de exibição para a mesma parte do arquivo mapeado na memória, criando assim memórias simultâneas.</span><span class="sxs-lookup"><span data-stu-id="840b7-119">You can also create multiple views to the same part of the memory-mapped file, thereby creating concurrent memory.</span></span> <span data-ttu-id="840b7-120">Para que dois modos de exibição permaneçam simultâneos, precisam ser criados usando o mesmo arquivo de memória mapeada.</span><span class="sxs-lookup"><span data-stu-id="840b7-120">For two views to remain concurrent, they have to be created from the same memory-mapped file.</span></span>  
  
 <span data-ttu-id="840b7-121">Vários modos de exibição também poderão ser necessários se o arquivo for maior que o tamanho do espaço de memória lógica do aplicativo disponível para o mapeamento de memória (2GB em um computador de 32 bits).</span><span class="sxs-lookup"><span data-stu-id="840b7-121">Multiple views may also be necessary if the file is greater than the size of the application’s logical memory space available for memory mapping (2 GB on a 32-bit computer).</span></span>  
  
 <span data-ttu-id="840b7-122">Há dois tipos de modos de exibição: modo de exibição de acesso por fluxo e modo de exibição de acesso aleatório.</span><span class="sxs-lookup"><span data-stu-id="840b7-122">There are two types of views: stream access view and random access view.</span></span> <span data-ttu-id="840b7-123">Use os modos de exibição de acesso por fluxo para acessos sequenciais a um arquivo. Isso é recomendado para arquivos não persistentes e IPCs.</span><span class="sxs-lookup"><span data-stu-id="840b7-123">Use stream access views for sequential access to a file; this is recommended for non-persisted files and IPC.</span></span> <span data-ttu-id="840b7-124">A preferência é para os modos de exibição de acessos aleatórios para trabalhos com arquivos persistentes.</span><span class="sxs-lookup"><span data-stu-id="840b7-124">Random access views are preferred for working with persisted files.</span></span>  
  
 <span data-ttu-id="840b7-125">Os arquivos mapeados na memória são acessados pelo gerenciador de memória do sistema operacional, então o arquivo é automaticamente particionado em um número de páginas e acessado conforme a necessidade.</span><span class="sxs-lookup"><span data-stu-id="840b7-125">Memory-mapped files are accessed through the operating system’s memory manager, so the file is automatically partitioned into a number of pages and accessed as needed.</span></span> <span data-ttu-id="840b7-126">Não é preciso lidar com o gerenciamento de memória por conta própria.</span><span class="sxs-lookup"><span data-stu-id="840b7-126">You do not have to handle the memory management yourself.</span></span>  
  
 <span data-ttu-id="840b7-127">A ilustração a seguir mostra como vários processos podem ter modos de exibição variados e sobrepostos para o mesmo arquivo mapeado na memória ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="840b7-127">The following illustration shows how multiple processes can have multiple and overlapping views to the same memory-mapped file at the same time.</span></span>

 <span data-ttu-id="840b7-128">A seguinte imagem mostra várias exibições sobrepostas em um arquivo mapeado em memória:</span><span class="sxs-lookup"><span data-stu-id="840b7-128">The following image shows multiple and overlapped views to a memory-mapped file:</span></span>  
  
 ![Captura de tela que mostra as exibições em um arquivo mapeado em memória.](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a><span data-ttu-id="840b7-130">Programar com arquivos mapeados na memória</span><span class="sxs-lookup"><span data-stu-id="840b7-130">Programming with Memory-Mapped Files</span></span>  
 <span data-ttu-id="840b7-131">A tabela a seguir orienta como usar objetos de arquivos mapeados na memória e os membros deles.</span><span class="sxs-lookup"><span data-stu-id="840b7-131">The following table provides a guide for using memory-mapped file objects and their members.</span></span>  
  
|<span data-ttu-id="840b7-132">Tarefa</span><span class="sxs-lookup"><span data-stu-id="840b7-132">Task</span></span>|<span data-ttu-id="840b7-133">Métodos ou propriedades a serem usados</span><span class="sxs-lookup"><span data-stu-id="840b7-133">Methods or properties to use</span></span>|  
|----------|----------------------------------|  
|<span data-ttu-id="840b7-134">Para obter um objeto <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> de um arquivo no disco que representa um arquivo persistente mapeado na memória.</span><span class="sxs-lookup"><span data-stu-id="840b7-134">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a persisted memory-mapped file from a file on disk.</span></span>|<span data-ttu-id="840b7-135">Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="840b7-135"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="840b7-136">Para obter um objeto <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> que representa um arquivo não persistente mapeado na memória (não associado a um arquivo no disco).</span><span class="sxs-lookup"><span data-stu-id="840b7-136">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a non-persisted memory-mapped file (not associated with a file on disk).</span></span>|<span data-ttu-id="840b7-137">Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="840b7-137"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> method.</span></span><br /><br /> <span data-ttu-id="840b7-138">- ou -</span><span class="sxs-lookup"><span data-stu-id="840b7-138">- or -</span></span><br /><br /> <span data-ttu-id="840b7-139">Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="840b7-139"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="840b7-140">Para obter um objeto <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> de um arquivo mapeado na memória existente (persistente ou não persistente).</span><span class="sxs-lookup"><span data-stu-id="840b7-140">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object of an existing memory-mapped file (either persisted or non-persisted).</span></span>|<span data-ttu-id="840b7-141">Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="840b7-141"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="840b7-142">Para obter um objeto <xref:System.IO.UnmanagedMemoryStream> para uma exibição de acesso em sequência para o arquivo mapeado na memória.</span><span class="sxs-lookup"><span data-stu-id="840b7-142">To obtain a <xref:System.IO.UnmanagedMemoryStream> object for a sequentially accessed view to the memory-mapped file.</span></span>|<span data-ttu-id="840b7-143">Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="840b7-143"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="840b7-144">Para obter um objeto <xref:System.IO.UnmanagedMemoryAccessor> para uma exibição de acesso aleatório para um arquivo mapeado na memória.</span><span class="sxs-lookup"><span data-stu-id="840b7-144">To obtain a <xref:System.IO.UnmanagedMemoryAccessor> object for a random access view to a memory-mapped fie.</span></span>|<span data-ttu-id="840b7-145">Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="840b7-145"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="840b7-146">Para obter um objeto <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> a ser usado com um código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="840b7-146">To obtain a <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> object to use with unmanaged code.</span></span>|<span data-ttu-id="840b7-147">Propriedade <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="840b7-147"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="840b7-148">- ou -</span><span class="sxs-lookup"><span data-stu-id="840b7-148">- or -</span></span><br /><br /> <span data-ttu-id="840b7-149">Propriedade <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="840b7-149"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="840b7-150">- ou -</span><span class="sxs-lookup"><span data-stu-id="840b7-150">- or -</span></span><br /><br /> <span data-ttu-id="840b7-151">Propriedade <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="840b7-151"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span>|  
|<span data-ttu-id="840b7-152">Para atrasar a alocação de memória até que uma exibição seja criada (somente arquivos não persistentes).</span><span class="sxs-lookup"><span data-stu-id="840b7-152">To delay allocating memory until a view is created (non-persisted files only).</span></span><br /><br /> <span data-ttu-id="840b7-153">Para determinar o tamanho de página atual do sistema, use a propriedade <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="840b7-153">(To determine the current system page size, use the <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> property.)</span></span>|<span data-ttu-id="840b7-154">Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> com o valor <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="840b7-154"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> method with the <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> value.</span></span><br /><br /> <span data-ttu-id="840b7-155">- ou -</span><span class="sxs-lookup"><span data-stu-id="840b7-155">- or -</span></span><br /><br /> <span data-ttu-id="840b7-156">Métodos <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> que possuem uma enumeração <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> como parâmetro.</span><span class="sxs-lookup"><span data-stu-id="840b7-156"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods that have a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> enumeration as a parameter.</span></span>|  
  
### <a name="security"></a><span data-ttu-id="840b7-157">Segurança</span><span class="sxs-lookup"><span data-stu-id="840b7-157">Security</span></span>  
 <span data-ttu-id="840b7-158">É possível aplicar os direitos de acesso ao criar um arquivo mapeado na memória usando os seguintes métodos que usam uma enumeração <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> como parâmetro:</span><span class="sxs-lookup"><span data-stu-id="840b7-158">You can apply access rights when you create a memory-mapped file, by using the following methods that take a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> enumeration as a parameter:</span></span>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="840b7-159">É possível especificar os direitos de acesso para abrir um arquivo mapeado na memória existente usando os métodos <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> que usam <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> como parâmetro.</span><span class="sxs-lookup"><span data-stu-id="840b7-159">You can specify access rights for opening an existing memory-mapped file by using the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> methods that take an <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> as a parameter.</span></span>  
  
 <span data-ttu-id="840b7-160">Além disso, é possível incluir um objeto <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> que contém regras de acesso predefinidas.</span><span class="sxs-lookup"><span data-stu-id="840b7-160">In addition, you can include a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> object that contains predefined access rules.</span></span>  
  
 <span data-ttu-id="840b7-161">Para aplicar as regras de acesso novas ou modificadas a um arquivo mapeado na memória, use o método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A>.</span><span class="sxs-lookup"><span data-stu-id="840b7-161">To apply new or changed access rules to a memory-mapped file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> method.</span></span> <span data-ttu-id="840b7-162">Para recuperar as regras de acesso ou de auditoria de um arquivo existente, use o método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A>.</span><span class="sxs-lookup"><span data-stu-id="840b7-162">To retrieve access or audit rules from an existing file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="840b7-163">Exemplos</span><span class="sxs-lookup"><span data-stu-id="840b7-163">Examples</span></span>  
  
### <a name="persisted-memory-mapped-files"></a><span data-ttu-id="840b7-164">Arquivos persistentes mapeados na memória</span><span class="sxs-lookup"><span data-stu-id="840b7-164">Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="840b7-165">Os métodos <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> criam um arquivo mapeado na memória de um arquivo existente no disco.</span><span class="sxs-lookup"><span data-stu-id="840b7-165">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> methods create a memory-mapped file from an existing file on disk.</span></span>  
  
 <span data-ttu-id="840b7-166">O exemplo a seguir cria uma exibição de mapeamento na memória de parte de um arquivo muito grande e manipula uma porção dele.</span><span class="sxs-lookup"><span data-stu-id="840b7-166">The following example creates a memory-mapped view of a part of an extremely large file and manipulates a portion of it.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
  
 <span data-ttu-id="840b7-167">O exemplo a seguir abre o mesmo arquivo mapeado na memória para outro processo.</span><span class="sxs-lookup"><span data-stu-id="840b7-167">The following example opens the same memory-mapped file for another process.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a><span data-ttu-id="840b7-168">Arquivos não persistentes mapeados na memória</span><span class="sxs-lookup"><span data-stu-id="840b7-168">Non-Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="840b7-169">Os métodos <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> e <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> criam um arquivo mapeado na memória que não está mapeado para um arquivo existente no disco.</span><span class="sxs-lookup"><span data-stu-id="840b7-169">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> and <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods create a memory-mapped file that is not mapped to an existing file on disk.</span></span>  
  
 <span data-ttu-id="840b7-170">O exemplo a seguir consiste de três processos separados (aplicativos de console) que gravam valores booleanos em um arquivo mapeado na memória.</span><span class="sxs-lookup"><span data-stu-id="840b7-170">The following example consists of three separate processes (console applications) that write Boolean values to a memory-mapped file.</span></span> <span data-ttu-id="840b7-171">Ocorre a seguinte sequência de ações:</span><span class="sxs-lookup"><span data-stu-id="840b7-171">The following sequence of actions occur:</span></span>  
  
1. <span data-ttu-id="840b7-172">O `Process A` cria o arquivo mapeado na memória e grava um valor para ele.</span><span class="sxs-lookup"><span data-stu-id="840b7-172">`Process A` creates the memory-mapped file and writes a value to it.</span></span>  
  
2. <span data-ttu-id="840b7-173">O `Process B` abre o arquivo mapeado na memória e grava um valor para ele.</span><span class="sxs-lookup"><span data-stu-id="840b7-173">`Process B` opens the memory-mapped file and writes a value to it.</span></span>  
  
3. <span data-ttu-id="840b7-174">O `Process C` abre o arquivo mapeado na memória e grava um valor para ele.</span><span class="sxs-lookup"><span data-stu-id="840b7-174">`Process C` opens the memory-mapped file and writes a value to it.</span></span>  
  
4. <span data-ttu-id="840b7-175">O `Process A` lê e exibe os valores do arquivo mapeado na memória.</span><span class="sxs-lookup"><span data-stu-id="840b7-175">`Process A` reads and displays the values from the memory-mapped file.</span></span>  
  
5. <span data-ttu-id="840b7-176">Após o `Process A` concluir com o arquivo mapeado na memória, o arquivo é imediatamente recuperado pela coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="840b7-176">After `Process A` is finished with the memory-mapped file, the file is immediately reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="840b7-177">Para executar este exemplo, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="840b7-177">To run this example, do the following:</span></span>  
  
1. <span data-ttu-id="840b7-178">Compile os aplicativos e abra três janelas de Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="840b7-178">Compile the applications and open three Command Prompt windows.</span></span>  
  
2. <span data-ttu-id="840b7-179">Na primeira janela do prompt, execute o `Process A`.</span><span class="sxs-lookup"><span data-stu-id="840b7-179">In the first Command Prompt window, run `Process A`.</span></span>  
  
3. <span data-ttu-id="840b7-180">Na segunda janela, execute o `Process B`.</span><span class="sxs-lookup"><span data-stu-id="840b7-180">In the second Command Prompt window, run `Process B`.</span></span>  
  
4. <span data-ttu-id="840b7-181">Retorne ao `Process A` e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="840b7-181">Return to `Process A` and press ENTER.</span></span>  
  
5. <span data-ttu-id="840b7-182">Na terceira janela do prompt, execute o `Process C`.</span><span class="sxs-lookup"><span data-stu-id="840b7-182">In the third Command Prompt window, run `Process C`.</span></span>  
  
6. <span data-ttu-id="840b7-183">Retorne ao `Process A` e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="840b7-183">Return to `Process A` and press ENTER.</span></span>  
  
 <span data-ttu-id="840b7-184">A saída do `Process A` é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="840b7-184">The output of `Process A` is as follows:</span></span>  
  
```  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 <span data-ttu-id="840b7-185">**Processo A**</span><span class="sxs-lookup"><span data-stu-id="840b7-185">**Process A**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 <span data-ttu-id="840b7-186">**Processo B**</span><span class="sxs-lookup"><span data-stu-id="840b7-186">**Process B**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 <span data-ttu-id="840b7-187">**Processo C**</span><span class="sxs-lookup"><span data-stu-id="840b7-187">**Process C**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="840b7-188">Consulte também</span><span class="sxs-lookup"><span data-stu-id="840b7-188">See also</span></span>

- [<span data-ttu-id="840b7-189">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="840b7-189">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
