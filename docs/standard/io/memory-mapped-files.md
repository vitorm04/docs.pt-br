---
title: "Arquivos mapeados na memória"
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
helpviewer_keywords:
- memory-mapped files
- inter-process communiation
ms.assetid: a483d1b5-64aa-45b6-86ef-11b859f7f02e
caps.latest.revision: "24"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2602d431aada7b3e0ee226eed319903492022ae9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="memory-mapped-files"></a>Arquivos mapeados na memória
Um arquivo mapeado pela memória tem o conteúdo de um arquivo em memória virtual. Esse mapeamento entre um espaço de arquivo e memória permite que um aplicativo, incluindo vários processos, modifique o arquivo, ler e gravar diretamente para a memória. Começando com o [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], você pode usar código gerenciado para acessar arquivos mapeados na memória da mesma maneira que funções nativas do Windows acessar arquivos mapeados na memória, conforme descrito em [Managing Memory-Mapped arquivos Win32](http://go.microsoft.com/fwlink/?linkid=180801).  
  
 Há dois tipos de arquivos mapeados na memória:  
  
-   Arquivos de memória mapeada persistentes  
  
     Arquivos persistentes são arquivos mapeados na memória que estão associados um arquivo de origem em um disco. Quando a última terminar o processo de trabalho com o arquivo, os dados são salvos no arquivo de origem no disco. Esses arquivos mapeados na memória são adequados para trabalhar com arquivos de origem muito grande.  
  
-   Não persistente arquivos mapeados na memória  
  
     Arquivos não persistente são arquivos mapeados na memória que não estão associados um arquivo em um disco. Quando a última terminar o processo de trabalho com o arquivo, os dados serão perdidos e o arquivo é recuperado pela coleta de lixo. Esses arquivos são adequados para a criação de memória compartilhada para comunicação entre processos (IPC).  
  
## <a name="processes-views-and-managing-memory"></a>Processos, modos de exibição e gerenciamento de memória  
 Arquivos mapeados na memória podem ser compartilhados entre vários processos. Processos podem mapear para o mesmo arquivo de mapeamento de memória usando um nome comum, que é atribuído pelo processo que criou o arquivo.  
  
 Para trabalhar com um arquivo de mapeamento de memória, você deve criar uma exibição de todo o arquivo de memória mapeada ou parte dela. Você também pode criar vários modos de exibição para a mesma parte do arquivo de mapeamento de memória, criando assim simultâneas de memória. Dois modos de exibição permanecer simultâneas, precisam ser criados a partir do mesmo arquivo de memória mapeada.  
  
 Vários modos de exibição também podem ser necessários se o arquivo for maior que o tamanho do espaço de memória lógica do aplicativo disponível para mapeamento (2 GB em um computador de 32 bits) de memória.  
  
 Há dois tipos de modos de exibição: modo de acesso e o modo de acesso aleatório de fluxo. Usar exibições de acesso de fluxo para acesso sequencial para um arquivo. Isso é recomendado para arquivos persistentes e IPC. Modos de exibição de acesso aleatório são preferenciais para trabalhar com arquivos persistentes.  
  
 Arquivos mapeados na memória são acessados por meio do Gerenciador de memória do sistema operacional, para que o arquivo é automaticamente particionado em um número de páginas e acessado conforme necessário. Você não precisa lidar com o gerenciamento de memória por conta própria.  
  
 A ilustração a seguir mostra como vários processos podem ter vários e sobreposição de modos de exibição para o mesmo arquivo de mapeamento de memória ao mesmo tempo.  
  
 ![Modos de exibição mostra uma memória &#45; o arquivo mapeado. ] (../../../docs/standard/io/media/memmappersisted.png "MemMapPersisted")  
Várias e overlapped modos de exibição para um arquivo de memória mapeada  
  
## <a name="programming-with-memory-mapped-files"></a>Programando com arquivos mapeados na memória  
 A tabela a seguir fornece um guia para usar objetos de arquivos mapeados na memória e seus membros.  
  
|Tarefa|Métodos ou propriedades a serem usadas|  
|----------|----------------------------------|  
|Para obter um <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objeto que representa um arquivo de mapeamento de memória persistente de um arquivo no disco.|Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>.|  
|Para obter um <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objeto que representa um persistentes arquivo mapeado em memória (não associado a um arquivo no disco).|Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>.<br /><br /> - ou -<br /><br /> Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>.|  
|Para obter um <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objeto de um mapeamento de memória arquivo existente (persistente ou não persistente).|Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType>.|  
|Para obter um <xref:System.IO.UnmanagedMemoryStream> objeto para uma exibição acessado em sequência para o arquivo de mapeamento de memória.|Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType>.|  
|Para obter um <xref:System.IO.UnmanagedMemoryAccessor> de objeto para um modo de exibição de acesso aleatório para uma memória mapeada CAM.|Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType>.|  
|Para obter um <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> objeto a ser usado com código não gerenciado.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType>propriedade.<br /><br /> - ou -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>propriedade.<br /><br /> - ou -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>propriedade.|  
|Para atrasar a alocação de memória até que uma exibição é criada (somente arquivos não persistente).<br /><br /> (Para determinar o tamanho de página atual do sistema, use o <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> propriedade.)|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A>método com o <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> valor.<br /><br /> - ou -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A>os métodos que possuem um <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> enumeração como um parâmetro.|  
  
### <a name="security"></a>Segurança  
 Você pode aplicar os direitos de acesso quando você cria um arquivo de mapeamento de memória, usando os seguintes métodos que usam um <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> enumeração como um parâmetro:  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 Você pode especificar os direitos de acesso para abrir um arquivo de mapeamento de memória existente usando o <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> métodos que usam um <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> como um parâmetro.  
  
 Além disso, você pode incluir um <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> objeto que contém as regras de acesso predefinidos.  
  
 Para aplicar regras de acesso de novo ou alterado para um arquivo de mapeamento de memória, use o <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> método. Para recuperar o acesso ou regras de um arquivo existente de auditoria, use o <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> método.  
  
## <a name="examples"></a>Exemplos  
  
### <a name="persisted-memory-mapped-files"></a>Arquivos de memória mapeada persistentes  
 O <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> métodos de criam um arquivo de mapeamento de memória de um arquivo existente no disco.  
  
 O exemplo a seguir cria uma exibição de mapeamento de memória de uma parte de um arquivo muito grande e manipula uma parte dele.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
  
 O exemplo a seguir abre o mesmo arquivo de memória mapeada para outro processo.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a>Não persistente arquivos mapeados na memória  
 O <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> e <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> métodos criam um arquivo de mapeamento de memória que não está mapeado para um arquivo existente no disco.  
  
 O exemplo a seguir consiste em três processos separados (aplicativos de console) que gravar valores booleanos em um arquivo de mapeamento de memória. A seguinte sequência de ações ocorrem:  
  
1.  `Process A`cria o arquivo de mapeamento de memória e grava um valor para ele.  
  
2.  `Process B`Abre o arquivo de mapeamento de memória e grava um valor para ele.  
  
3.  `Process C`Abre o arquivo de mapeamento de memória e grava um valor para ele.  
  
4.  `Process A`lê e exibe os valores do arquivo de mapeamento de memória.  
  
5.  Depois de `Process A` terminou com o arquivo de mapeamento de memória, o arquivo imediatamente é recuperado pela coleta de lixo.  
  
 Para executar este exemplo, faça o seguinte:  
  
1.  Compilar aplicativos e abra três janelas de Prompt de comando.  
  
2.  Na primeira janela de Prompt de comando, execute `Process A`.  
  
3.  Na segunda janela do Prompt de comando, execute `Process B`.  
  
4.  Retorne ao `Process A` e pressione ENTER.  
  
5.  Na terceira janela de Prompt de comando, execute `Process C`.  
  
6.  Retorne ao `Process A` e pressione ENTER.  
  
 A saída de `Process A` é o seguinte:  
  
```  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 **Processo**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 **Processo B**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 **Processo C**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)
