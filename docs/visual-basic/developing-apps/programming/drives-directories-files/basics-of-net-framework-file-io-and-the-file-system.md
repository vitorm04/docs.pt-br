---
title: "No&#231;&#245;es b&#225;sicas do .NET Framework do arquivo I-O e o sistema de arquivos (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "acesso a arquivos, e/s de arquivo no Visual Basic"
  - "atributos de arquivo, determinando"
  - "fluxos, operações fundamentais"
  - "permissões de arquivo"
  - "fluxos"
  - "fluxos, definição"
ms.assetid: 49d837c0-cf28-416f-8606-4d83d7b479ef
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No&#231;&#245;es b&#225;sicas de E/S de arquivo do .NET Framework e o sistema de arquivos (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Classes de <xref:System.IO> namespace são usados para trabalhar com unidades, arquivos e diretórios.  
  
 O <xref:System.IO> namespace contém o <xref:System.IO.File> e <xref:System.IO.Directory> classes, que fornecem o [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] funcionalidade que manipula arquivos e pastas. Como os métodos desses objetos são estáticos ou membros compartilhados, você pode usá-los diretamente sem criar uma instância da classe primeiro. Associado com essas classes são o <xref:System.IO.FileInfo> e <xref:System.IO.DirectoryInfo> classes, que serão familiares aos usuários do `My` recurso. Para usar essas classes, você deve totalmente qualificar os nomes ou importar os namespaces apropriados, incluindo o `Imports` declarações no início do código afetado. Para obter mais informações, consulte [instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
> [!NOTE]
>  Outros tópicos nesta seção usam o `My.Computer.FileSystem` do objeto, em vez de `System.IO` classes para trabalhar com unidades, arquivos e diretórios. O `My.Computer.FileSystem` objeto destina-se principalmente para uso em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programas. `System.IO` classes são destinadas a uso por qualquer linguagem que ofereça suporte a [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)], incluindo [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
## <a name="definition-of-a-stream"></a>Definição de um fluxo  
 O [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] usa fluxos para oferecer suporte a leitura e gravação em arquivos. Você pode pensar um fluxo como um conjunto unidimensional de dados contíguos, que tem um início e fim, e onde o cursor indica a posição atual no fluxo.  
  
 ![Cursor mostra a posição atual no fluxo de arquivos.](../../../../visual-basic/developing-apps/programming/drives-directories-files/media/filestream.png "FileStream")  
  
## <a name="stream-operations"></a>Operações de fluxo  
 Os dados contidos no fluxo podem vir da memória, um arquivo ou um soquete TCP/IP. Fluxos têm operações fundamentais que podem ser aplicadas a eles:  
  
-   Leitura. Você pode ler a partir de um fluxo, transferindo dados de fluxo em uma estrutura de dados, como uma cadeia de caracteres ou uma matriz de bytes.  
  
-   **Gravar**. Você pode escrever em um fluxo, transferindo dados de uma fonte de dados no fluxo.  
  
-   **Procurando**. Você pode consultar e modificar sua posição no fluxo.  
  
 Para obter mais informações, consulte [Composing Streams](../Topic/Composing%20Streams.md).  
  
## <a name="types-of-streams"></a>Tipos de fluxos  
 No [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)], um fluxo é representado pelo <xref:System.IO.Stream> classe, que forma a classe abstrata para todos os outros fluxos. Você não pode criar diretamente uma instância do <xref:System.IO.Stream> classe, mas deve usar uma das classes que ela implementa.  
  
 Há muitos tipos de fluxos, mas para fins de trabalhar com arquivos entrada/saída (e/s), os tipos mais importantes são o <xref:System.IO.FileStream> classe, que fornece uma maneira de ler e gravar arquivos, e o <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> classe, que fornece uma maneira de criar arquivos e diretórios em armazenamento isolado. Outros fluxos que podem ser usados ao trabalhar com e/s de arquivo incluem:  
  
-   <xref:System.IO.BufferedStream>  
  
-   <xref:System.Security.Cryptography.CryptoStream>  
  
-   <xref:System.IO.MemoryStream>  
  
-   <xref:System.Net.Sockets.NetworkStream>.  
  
 A tabela a seguir lista tarefas normalmente executadas com um fluxo:  
  
|||  
|-|-|  
|Para|Consulte|  
|Ler e gravar em um arquivo de dados|[Como: ler e gravar em um arquivo de dados recém-criado](../Topic/How%20to:%20Read%20and%20Write%20to%20a%20Newly%20Created%20Data%20File.md)|  
|Ler texto de um arquivo|[Como: ler texto de um arquivo](../Topic/How%20to:%20Read%20Text%20from%20a%20File.md)|  
|Gravar texto em um arquivo|[Como: gravar texto em um arquivo](../Topic/How%20to:%20Write%20Text%20to%20a%20File.md)|  
|Ler caracteres de uma cadeia de caracteres|[Como: ler caracteres de uma cadeia de caracteres](../Topic/How%20to:%20Read%20Characters%20from%20a%20String.md)|  
|Gravar caracteres em uma cadeia de caracteres|[Como: gravar uma cadeia de caracteres](../Topic/How%20to:%20Write%20Characters%20to%20a%20String.md)|  
|Criptografar dados|[Criptografando dados](../Topic/Encrypting%20Data.md)|  
|Descriptografar dados|[Descriptografando dados](../Topic/Decrypting%20Data.md)|  
  
## <a name="file-access-and-attributes"></a>Acesso a arquivos e atributos  
 Você pode controlar como os arquivos são criados, aberto e compartilhada com o <xref:System.IO.FileAccess>, <xref:System.IO.FileMode>, e <xref:System.IO.FileShare> enumerações, que contêm os sinalizadores usados pelos construtores do <xref:System.IO.FileStream> classe. Por exemplo, quando você abre ou cria um novo <xref:System.IO.FileStream>, o <xref:System.IO.FileMode> enumeração permite especificar se o arquivo é aberto para acrescentar, se um novo arquivo for criado se o arquivo especificado não existir, se o arquivo será substituído e assim por diante.  
  
 O <xref:System.IO.FileAttributes> enumeração permite a coleta de informações específicas do arquivo. O <xref:System.IO.FileAttributes> enumeração retorna os atributos armazenados do arquivo, como se ele está compactado, criptografado, oculto, somente leitura, um arquivo, um diretório, um arquivo de sistema ou um arquivo temporário.  
  
 A tabela a seguir lista as tarefas que envolvem o acesso a arquivos e atributos de arquivo:  
  
|||  
|-|-|  
|**Para**|**Consulte**|  
|Abrir e acrescentar texto em um arquivo de log|[Como: abrir e anexar um arquivo de Log](../Topic/How%20to:%20Open%20and%20Append%20to%20a%20Log%20File.md)|  
|Determinar os atributos de um arquivo|<xref:System.IO.FileAttributes>|  
  
## <a name="file-permissions"></a>Permissões de arquivo  
 Controlando o acesso a arquivos e pastas pode ser feito com o <xref:System.Security.Permissions.FileIOPermission> classe. Isso pode ser especialmente importante para desenvolvedores trabalhando com Web Forms, que por padrão são executados no contexto de uma conta de usuário local especial denominada ASPNET, que é criado como parte do [!INCLUDE[vstecasp](../../../../visual-basic/developing-apps/programming/drives-directories-files/includes/vstecasp_md.md)] e [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] instalações. Quando tal um aplicativo solicita acesso a um recurso, a conta de usuário ASPNET tem permissões limitadas, que podem impedir que o usuário execute ações como gravar em um arquivo de um aplicativo da Web. Para obter mais informações, consulte [permissões de segurança](http://msdn.microsoft.com/pt-br/b03757b4-e926-4196-b738-3733ced2bda0), e o <xref:System.Security.Permissions.FileIOPermission>.  
  
## <a name="isolated-file-storage"></a>Armazenamento isolado de arquivo  
 Armazenamento isolado é uma tentativa de resolver problemas criados ao trabalhar com arquivos em que o usuário ou código pode carecer de permissões necessárias. Armazenamento isolado atribui a cada usuário um compartimento de dados, que pode conter uma ou mais lojas. Armazenamentos podem ser isolados uns dos outros por usuário e por assembly. Somente o usuário e o assembly que criou um armazenamento têm acesso a ele. Um armazenamento atua como um sistema de arquivos virtual completa — em um armazenamento, você pode criar e manipular pastas e arquivos.  
  
 A tabela a seguir lista as tarefas comumente associadas ao armazenamento isolado de arquivo.  
  
|||  
|-|-|  
|Para|Consulte|  
|Criar um armazenamento isolado|[Como: obter armazenamentos para o armazenamento isolado](../Topic/How%20to:%20Obtain%20Stores%20for%20Isolated%20Storage.md)|  
|Enumerar armazenamentos isolados|[Como: enumerar repositórios para armazenamento isolado](../Topic/How%20to:%20Enumerate%20Stores%20for%20Isolated%20Storage.md)|  
|Excluir um armazenamento isolado|[Como: excluir repositórios no armazenamento isolado](../Topic/How%20to:%20Delete%20Stores%20in%20Isolated%20Storage.md)|  
|Criar um arquivo ou diretório no armazenamento isolado|[Como: criar arquivos e diretórios em armazenamento isolado](../Topic/How%20to:%20Create%20Files%20and%20Directories%20in%20Isolated%20Storage.md)|  
|Localizar um arquivo no armazenamento isolado|[Como: localizar arquivos e diretórios existentes no armazenamento isolado](../Topic/How%20to:%20Find%20Existing%20Files%20and%20Directories%20in%20Isolated%20Storage.md)|  
|Ler ou gravar em um arquivo no armazenamento isolado|[Como: ler e gravar em arquivos no armazenamento isolado](../Topic/How%20to:%20Read%20and%20Write%20to%20Files%20in%20Isolated%20Storage.md)|  
|Excluir um arquivo ou diretório no armazenamento isolado|[Como: excluir arquivos e diretórios em armazenamento isolado](../Topic/How%20to:%20Delete%20Files%20and%20Directories%20in%20Isolated%20Storage.md)|  
  
## <a name="file-events"></a>Eventos de arquivo  
 O <xref:System.IO.FileSystemWatcher> componente permite observar alterações em arquivos e pastas em seu sistema ou em qualquer computador ao qual você tem acesso à rede. Por exemplo, se um arquivo é modificado, convém enviar um usuário um alerta que a alteração ocorreu. Quando ocorrem alterações, um ou mais eventos são gerados, armazenados em um buffer e enviados para o <xref:System.IO.FileSystemWatcher> componente para processamento.  
  
## <a name="see-also"></a>Consulte também  
 [Compondo fluxos](../Topic/Composing%20Streams.md)   
 [Arquivo e fluxo de e-S](../Topic/File%20and%20Stream%20I-O.md)   
 [E/s de arquivo assíncrona](../Topic/Asynchronous%20File%20I-O.md)   
 [Classes usadas em e/s de arquivo do .NET Framework e o sistema de arquivos (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/classes-used-in-net-framework-file-io-and-the-file-system.md)