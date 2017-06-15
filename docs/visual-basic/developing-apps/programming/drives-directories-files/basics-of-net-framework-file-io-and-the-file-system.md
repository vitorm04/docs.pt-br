---
title: "Noções básicas de E/S de arquivo do .NET Framework e o sistema de arquivos (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- file access, file I/O in Visual Basic
- file attributes, determining
- streams, fundamental operations
- file permissions
- streams
- streams, definition
ms.assetid: 49d837c0-cf28-416f-8606-4d83d7b479ef
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 16b71732272dacd6610b8b32eb74ff07fafec314
ms.contentlocale: pt-br
ms.lasthandoff: 06/15/2017

---
# <a name="basics-of-net-framework-file-io-and-the-file-system-visual-basic"></a>Noções básicas de E/S de arquivo do .NET Framework e o sistema de arquivos (Visual Basic)
As classes no namespace <xref:System.IO> são usadas para trabalhar com unidades, arquivos e diretórios.  
  
 O namespace <xref:System.IO> contém as classes <xref:System.IO.File> e <xref:System.IO.Directory>, que fornecem a funcionalidade [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] que manipula arquivos e diretórios. Como os métodos desses objetos são estáticos ou membros compartilhados, você pode usá-los diretamente sem antes criar uma instância da classe. Associadas a essas classes estão as classes <xref:System.IO.FileInfo> e <xref:System.IO.DirectoryInfo>, conhecidas pelos usuários do recurso `My`. Para usar essas classes, você deve qualificar totalmente os nomes ou importar os namespaces apropriados, incluindo as declarações `Imports` no início do código afetado. Para obter mais informações, consulte [Instrução Imports (tipo e namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
> [!NOTE]
>  Os outros tópicos nesta seção usam o objeto `My.Computer.FileSystem`, em vez das classes `System.IO`, para trabalhar com unidades, arquivos e diretórios. O objeto `My.Computer.FileSystem` destina-se principalmente para uso em programas do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]. As classes `System.IO` são destinadas para uso por qualquer linguagem que dê suporte ao [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], incluindo o [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
## <a name="definition-of-a-stream"></a>Definição de um fluxo  
 O [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] usa fluxos para dar suporte à leitura e gravação em arquivos. Você pode pensar em um fluxo como um conjunto unidimensional de dados contíguos, que tem um início e um fim e um local em que o cursor indica a posição atual no fluxo.  
  
 ![Cursor mostra a posição atual no fluxo de arquivos.](../../../../visual-basic/developing-apps/programming/drives-directories-files/media/filestream.gif "FileStream")  
  
## <a name="stream-operations"></a>Operações de fluxo  
 Os dados contidos no fluxo podem vir da memória, de um arquivo ou de um soquete TCP/IP. Os fluxos têm operações fundamentais que podem ser aplicadas a eles:  
  
-   Leitura. Você pode ler em um fluxo, transferindo dados do fluxo para uma estrutura de dados, como uma cadeia de caracteres ou uma matriz de bytes.  
  
-   **Gravação**. Você pode gravar em um fluxo, transferindo dados de uma fonte de dados para o fluxo.  
  
-   **Busca**. Você pode consultar e modificar a sua posição no fluxo.  
  
 Para obter mais informações, consulte [Compondo fluxos](https://msdn.microsoft.com/library/e4y2dch9).  
  
## <a name="types-of-streams"></a>Tipos de fluxos  
 No [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], um fluxo é representado pela classe <xref:System.IO.Stream>, que forma a classe abstrata para todos os outros fluxos. Você não pode criar diretamente uma instância da classe <xref:System.IO.Stream>, mas deve usar uma das classes que ela implementa.  
  
 Há muitos tipos de fluxos, porém, com a finalidade de trabalhar com entrada/saída (E/S) de arquivos, os tipos mais importantes são a classe <xref:System.IO.FileStream>, que fornece uma maneira de ler e gravar arquivos, e a classe <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>, que fornece uma maneira de criar arquivos e diretórios em armazenamento isolado. Outros fluxos que podem ser usados ao trabalhar com E/S de arquivo incluem:  
  
-   <xref:System.IO.BufferedStream>  
  
-   <xref:System.Security.Cryptography.CryptoStream>  
  
-   <xref:System.IO.MemoryStream>  
  
-   <xref:System.Net.Sockets.NetworkStream>.  
  
 A tabela a seguir lista as tarefas comumente realizadas com um fluxo:  
  
|Para|Consulte|
|---|---|   
|Ler e gravar em um arquivo de dados|[Como ler e gravar em um arquivo de dados recém-criado](https://msdn.microsoft.com/library/36b93480.aspx)|  
|Ler texto de um arquivo|[Como ler texto de um arquivo](https://msdn.microsoft.com/library/db5x7c0d.aspx)|  
|Gravar texto em um arquivo|[Como gravar texto em um arquivo](https://msdn.microsoft.com/library/6ka1wd3w.aspx)|  
|Ler caracteres de uma cadeia de caracteres|[Como ler caracteres de uma cadeia de caracteres](https://msdn.microsoft.com/library/9yyz8a6c.aspx)|  
|Gravar caracteres em uma cadeia de caracteres|[Como gravar caracteres em uma cadeia de caracteres](https://msdn.microsoft.com/library/z4kzt0dd.aspx)|  
|Criptografar dados|[Criptografando dados](https://msdn.microsoft.com/library/as0w18af.aspx)|  
|Descriptografar dados|[Descriptografando dados](https://msdn.microsoft.com/library/te15te69.aspx)|  
  
## <a name="file-access-and-attributes"></a>Acesso a arquivos e atributos  
 Você pode controlar como os arquivos são criados, abertos e compartilhados com as enumerações <xref:System.IO.FileAccess>, <xref:System.IO.FileMode> e <xref:System.IO.FileShare>, que contêm os sinalizadores usados pelos construtores da classe <xref:System.IO.FileStream>. Por exemplo, quando você abre ou cria uma nova <xref:System.IO.FileStream>, a enumeração <xref:System.IO.FileMode> permite especificar se o arquivo está aberto para acréscimos, se um novo arquivo será criado caso o arquivo especificado não exista, se o arquivo será substituído e assim por diante.  
  
 A enumeração <xref:System.IO.FileAttributes> habilita a coleta de informações específicas do arquivo. A enumeração <xref:System.IO.FileAttributes> retorna os atributos armazenados do arquivo, por exemplo, se ele é compactado, criptografado, oculto, somente leitura, um arquivo, um diretório, um arquivo de sistema ou um arquivo temporário.  
  
 A tabela a seguir lista as tarefas que envolvem o acesso a arquivos e atributos de arquivo:  
  
|Para|Consulte|  
|---|---|
|Abrir e acrescentar texto a um arquivo de log|[Como abrir e acrescentar a um arquivo de log](https://msdn.microsoft.com/library/3zc0w663.aspx)|  
|Determinar os atributos de um arquivo|<xref:System.IO.FileAttributes>|  
  
## <a name="file-permissions"></a>Permissões de arquivo  
 É possível controlar o acesso a arquivos e diretórios com a classe <xref:System.Security.Permissions.FileIOPermission>. Isso pode ser especialmente importante para desenvolvedores que trabalham com Web Forms, que, por padrão, são executados no contexto de uma conta de usuário local especial denominada ASPNET, que é criada como parte das instalações do [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] e [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Quando esse tipo de aplicativo solicita acesso a um recurso, a conta de usuário ASPNET tem permissões limitadas, que podem impedir que o usuário realize ações como gravar em um arquivo de um aplicativo Web. Para saber mais, confira [Permissões de segurança](http://msdn.microsoft.com/en-us/b03757b4-e926-4196-b738-3733ced2bda0) e <xref:System.Security.Permissions.FileIOPermission>.  
  
## <a name="isolated-file-storage"></a>Armazenamento isolado de arquivo  
 O armazenamento isolado é uma tentativa de resolver problemas criados ao trabalhar com arquivos em que o usuário ou código pode não ter as permissões necessárias. O armazenamento isolado atribui a cada usuário um compartimento de dados, que pode conter uma ou mais repositórios. Os repositórios podem ser isolados uns dos outros, por usuário e por assembly. Somente o usuário e o assembly que criou um repositório tem acesso a ele. Um repositório atua como um sistema de arquivos virtual completo. Você pode criar e manipular pastas e arquivos em um repositório.  
  
 A tabela a seguir lista as tarefas comumente associadas ao armazenamento isolado de arquivo.  
  
|Para|Consulte|
|---|---|  
|Criar um repositório isolado|[Como obter repositórios para o armazenamento isolado](https://msdn.microsoft.com/library/k48a6h13.aspx)|  
|Enumerar repositórios isolados|[Como enumerar repositórios para o armazenamento isolado](https://msdn.microsoft.com/library/c3dy613a.aspx)|  
|Excluir um repositório isolado|[Como excluir repositórios no armazenamento isolado](https://msdn.microsoft.com/library/5w71t104.aspx)|  
|Criar um arquivo ou diretório no armazenamento isolado|[Como criar arquivos e diretórios no armazenamento isolado](https://msdn.microsoft.com/library/6h2ws3ft.aspx)|  
|Localizar um arquivo no armazenamento isolado|[Como localizar arquivos e diretórios existentes no armazenamento isolado](https://msdn.microsoft.com/library/zd5e2z84.aspx)|  
|Ler ou gravar em um arquivo no armazenamento isolado|[Como ler e gravar em arquivos no armazenamento isolado](https://msdn.microsoft.com/library/xf96a1wz.aspx)|  
|Excluir um arquivo ou diretório no armazenamento isolado|[Como excluir arquivos e diretórios no armazenamento isolado](https://msdn.microsoft.com/library/kx3852wf.aspx)|  
  
## <a name="file-events"></a>Eventos de arquivo  
 O componente <xref:System.IO.FileSystemWatcher> permite observar alterações em arquivos e diretórios em seu sistema ou em qualquer computador em que você tem acesso à rede. Por exemplo, se um arquivo é modificado, convém enviar a um usuário um alerta sobre a alteração ocorrida. Quando ocorrem alterações, um ou mais eventos são acionados, armazenados em um buffer e enviados ao componente <xref:System.IO.FileSystemWatcher> para processamento.  
  
## <a name="see-also"></a>Consulte também  
 [Compondo fluxos](https://msdn.microsoft.com/library/e4y2dch9)   
 [E/S de arquivo e de fluxo](https://msdn.microsoft.com/library/k3352a4t)   
 [E/S de arquivo assíncrona](https://msdn.microsoft.com/library/kztecsys)   
 [Classes usadas em E/S de arquivo do .NET Framework e o sistema de arquivos (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/classes-used-in-net-framework-file-io-and-the-file-system.md)
