---
title: Tipos de isolamento
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
- cpp
helpviewer_keywords:
- storing data using isolated storage, accessing isolated storage
- storing data using isolated storage, isolation types
- authentication [.NET Framework], isolated storage
- assemblies [.NET Framework], identity
- isolated storage, accessing
- data storage using isolated storage, isolation types
- data storage using isolated storage, accessing isolated storage
- domain identity
- isolated storage, types
- user authentication, isolated storage
ms.assetid: 14812988-473f-44ae-b75f-fd5c2f21fb7b
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6b07c090a381925f5330a820214126a121d3790b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="types-of-isolation"></a>Tipos de isolamento
Acesso ao armazenamento isolado é sempre restrito ao usuário que o criou. Para implementar esse tipo de isolamento, o common language runtime usa a mesma noção de identidade de usuário que o sistema operacional reconhece, que é a identidade associada com o processo no qual o código está em execução quando o armazenamento é aberto. Essa identidade é uma identidade de usuário autenticado, mas a representação pode fazer com que a identidade do usuário atual para alterar dinamicamente.  
  
 Acesso ao armazenamento isolado também é restrito de acordo com a identidade associada com o domínio do aplicativo e o assembly ou com o conjunto sozinho. O tempo de execução obtém essas identidades das seguintes maneiras:  
  
-   Identidade de domínio representa a evidência do aplicativo, que, no caso de um aplicativo web pode ser a URL completa. Para código hospedado pelo shell, a identidade de domínio pode ser baseada no caminho de diretório de aplicativo. Por exemplo, se o executável será executado do caminho c:\Office\MyApp.exe., a identidade de domínio seria c:\Office\MyApp.exe..  
  
-   Identidade do assembly é a evidência do assembly. Isso pode vir de uma assinatura digital de criptografia, que pode ser o assembly [nome forte](../../../docs/framework/app-domains/strong-named-assemblies.md), no Editor de software do assembly, ou sua identidade URL. Se um assembly tiver um nome forte e uma identidade do Editor de software, a identidade do Editor de software é usada. Se o assembly vêm da Internet e não estiver assinado, a identidade de URL é usada. Para obter mais informações sobre assemblies de nomes fortes, consulte [programação com Assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md).  
  
-   Armazenamentos móveis se movem com um usuário que tem um perfil de usuário móvel. Arquivos são gravados em um diretório de rede e são baixados em qualquer computador, o usuário fizer logon. Para obter mais informações sobre perfis de usuário móvel, consulte <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>.  
  
 Combinando os conceitos de usuário, domínio e identidade do assembly, o armazenamento isolado pode isolar dados de maneiras a seguir, cada um deles tem seus próprios cenários de uso:  
  
-   [Isolamento por usuário e assembly](#UserAssembly)  
  
-   [Isolamento por usuário, domínio e assembly](#UserDomainAssembly)  
  
 Um desses isolamentos podem ser combinado com um perfil de usuário móvel. Para obter mais informações, consulte a seção [armazenamento isolado e Roaming](#Roaming).  
  
 A ilustração a seguir demonstra como armazenamentos são isolados em escopos diferentes.  
  
 ![Isolamento por usuário e assembly](../../../docs/standard/io/media/typesofisolation.gif "typesofisolation")  
Tipos de armazenamento isolado  
  
 Observe que, exceto armazenamentos móveis, armazenamento isolado é sempre implicitamente isolado por computador porque ele usa os recursos de armazenamento que são locais para um determinado computador.  
  
> [!IMPORTANT]
>  O armazenamento isolado não está disponível para aplicativos [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]. Em vez disso, use as classes de dados de aplicativos nos namespaces `Windows.Storage` incluídos na API [!INCLUDE[wrt](../../../includes/wrt-md.md)] para armazenar dados e arquivos locais. Para saber mais, confira [Dados de aplicativo](http://go.microsoft.com/fwlink/?LinkId=229175) no Centro de Desenvolvimento do Windows.  
  
<a name="UserAssembly"></a>   
## <a name="isolation-by-user-and-assembly"></a>Isolamento por usuário e Assembly  
 Quando o assembly que usa os dados armazena deve ser acessível de qualquer domínio de aplicativo, o isolamento pelo usuário e assembly é apropriado. Normalmente, nessa situação, o armazenamento isolado é usado para armazenar dados que se aplica em vários aplicativos e não estão vinculados a qualquer aplicativo específico, como o nome do usuário ou informações de licença. Para acessar o armazenamento isolado por usuário e assembly, o código deve ser confiável para transferir informações entre aplicativos. Normalmente, isolamento pelo usuário e assembly é permitido em intranets, mas não na Internet. Chamando estático <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType> método e passar um usuário e um assembly <xref:System.IO.IsolatedStorage.IsolatedStorageScope> retorna um armazenamento com esse tipo de isolamento.  
  
 O exemplo de código a seguir recupera um armazenamento que é isolado por usuário e assembly. O armazenamento pode ser acessado por meio de `isoFile` objeto.  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 Para obter um exemplo que usa os parâmetros de evidência, consulte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>.  
  
 O <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> método está disponível como um atalho, conforme mostrado no exemplo de código a seguir. Este atalho não pode ser usado para abrir armazenamentos capazes de roaming; Use <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> nesses casos.  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>   
## <a name="isolation-by-user-domain-and-assembly"></a>Isolamento por usuário, domínio e Assembly  
 Se seu aplicativo usa um assembly de terceiros que exige um armazenamento de dados particulares, você pode usar o armazenamento isolado para armazenar os dados privados. Isolamento por usuário, domínio e assembly garante que somente o código em um determinado assembly pode acessar os dados e somente quando o assembly é usado pelo aplicativo que estava em execução quando o assembly criado o repositório e somente quando o usuário para quem o armazenamento foi criado executa o  aplicativo. Isolamento por usuário, domínio e assembly mantém o assembly de terceiros de vazamento de dados para outros aplicativos. Esse tipo de isolamento deve ser a opção padrão, se você souber que deseja usar armazenamento isolado e não tiver certeza de qual tipo de isolamento para usar. Chamando estático <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> método <xref:System.IO.IsolatedStorage.IsolatedStorageFile> e passando um usuário, domínio e assembly <xref:System.IO.IsolatedStorage.IsolatedStorageScope> retorna um armazenamento com esse tipo de isolamento.  
  
 O exemplo de código a seguir recupera um armazenamento isolado por usuário, domínio e assembly. O armazenamento pode ser acessado por meio de `isoFile` objeto.  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 Outro método está disponível como um atalho, conforme mostrado no exemplo de código a seguir. Este atalho não pode ser usado para abrir armazenamentos capazes de roaming; Use <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> nesses casos.  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>   
## <a name="isolated-storage-and-roaming"></a>Armazenamento isolado e Roaming  
 Perfis de usuário móvel são um recurso do Windows que permite que um usuário configure uma identidade em uma rede e usar essa identidade para fazer logon em qualquer computador da rede, mantendo todas as configurações personalizadas. Um assembly que usa armazenamento isolado pode especificar que o armazenamento isolado do usuário deve mover com o perfil de usuário móvel. Roaming pode ser usado em conjunto com o isolamento pelo usuário e assembly ou com isolamento de usuário, domínio e assembly. Se um escopo móvel não for usado, armazenamentos não entrará em roaming mesmo se um perfil de usuário móvel é usado.  
  
 O exemplo de código a seguir recupera um armazenamento móvel isolado por usuário e assembly. O armazenamento pode ser acessado por meio de `isoFile` objeto.  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 Um escopo de domínio pode ser adicionado para criar um armazenamento móvel isolado por usuário, domínio e aplicativo. O exemplo de código a seguir demonstra isso.  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
 [Armazenamentos isolado](../../../docs/standard/io/isolated-storage.md)
