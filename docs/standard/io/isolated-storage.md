---
title: Armazenamentos isolado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data storage using isolated storage
- stores
- storing data using isolated storage
- isolated storage
- location of isolated storage in file system
- standardizing storage systems
- storing data using isolated storage, when not to use
- code, isolated storage
- isolated storage, options
- data storage using isolated storage, when not to use
- storing data using isolated storage, options
- isolated storage, when not to use
- data storage using isolated storage, options
- isolation
ms.assetid: aff939d7-9e49-46f2-a8cd-938d3020e94e
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0048c1946e5df59340bed211c5dbb81075047260
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2018
---
# <a name="isolated-storage"></a>Armazenamentos isolado
<a name="top"></a> Para aplicativos [!INCLUDE[desktop_appname](../../../includes/desktop-appname-md.md)], o armazenamento isolado é um mecanismo de armazenamento de dados que proporciona isolamento e segurança ao definir formas padronizadas de associar código a dados salvos. A padronização também fornece outros benefícios. Os administradores podem usar as ferramentas desenvolvidas para manipular armazenamentos isolados para configurar espaço de armazenamento de arquivos, definir políticas de segurança e excluir dados não utilizados. Com armazenamentos isolados, seu código não precisa mais de caminhos exclusivos para especificar locais seguros na sistema de arquivos e os dados são protegidos de outros aplicativos que só têm acesso a armazenamentos isolados. Informações embutidas em código que indicam onde a área de armazenamento de um aplicativo se encontra são desnecessárias.  
  
> [!IMPORTANT]
>  O armazenamento isolado não está disponível para aplicativos [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]. Em vez disso, use as classes de dados de aplicativos nos namespaces `Windows.Storage` incluídos na API [!INCLUDE[wrt](../../../includes/wrt-md.md)] para armazenar dados e arquivos locais. Para saber mais, confira [Dados de aplicativo](/previous-versions/windows/apps/hh464917(v=win.10)) no Centro de Desenvolvimento do Windows.  
  
 Esse tópico contém as seguintes seções:  
  
-   [Compartimentos e repositórios de dados](#data_compartments_and_stores)  
  
-   [Cotas de armazenamento isolado](#quotas)  
  
-   [Acesso seguro](#secure_access)  
  
-   [Uso permitido e riscos de segurança](#allowed_usage)  
  
-   [Locais de armazenamento isolados](#isolated_storage_locations)  
  
-   [Criar, enumerar e excluir armazenamento isolado](#isolated_storage_tasks)  
  
-   [Cenários para armazenamento isolado](#scenarios_for_isolated_storage)  
  
-   [Tópicos relacionados](#related_topics)  
  
-   [Referência](#reference)  
  
<a name="data_compartments_and_stores"></a>   
## <a name="data-compartments-and-stores"></a>Compartimentos e Repositórios de Dados  
 Quando um aplicativo armazena dados em um arquivo, o nome do arquivo e o local de armazenamento devem ser escolhidos cuidadosamente para minimizar a possibilidade de o local de armazenamento ser conhecido por outro aplicativo e, portanto, tornar-se vulnerável a corrompimento. Sem um sistema padrão para gerenciar esses problemas, o desenvolvimento de técnicas ad hoc que minimizam conflitos de armazenamento pode ser complexo e os resultados podem não ser confiáveis.  
  
 Com armazenamento isolado, os dados são sempre isolados pelo usuário e pelo assembly. Credenciais como a origem ou o nome forte do assembly determinam a identidade do assembly. Os dados também podem ser isolados por domínio de aplicativo, usando credenciais semelhantes.  
  
 Quando você usa armazenamento isolado, os aplicativos salvam dados em um compartimento de dados específico que está associado a algum aspecto da identidade do código, como seu site, o editor ou a assinatura. O compartimento de dados é uma abstração, não um local específico de armazenamento; ele consiste em um ou mais arquivos de armazenamento isolados, chamados de repositórios, que contêm os locais reais dos diretórios em que os dados estão armazenados. Por exemplo, um aplicativo pode ter um compartimento de dados associado a ele, e um diretório de sistema de arquivos implementaria o repositório que de fato preserva os dados para o aplicativo. Os dados salvos no repositório podem ser qualquer tipo de dados, desde informações de preferências do usuário até o estado do aplicativo. Para o desenvolvedor, o local do compartimento de dados é transparente. Os repositórios normalmente residem no cliente, mas um aplicativo de servidor pode usar repositórios isolados para armazenar informações que personificam o usuário em cujo nome ele está funcionando. Armazenamentos isolados também podem armazenar informações em um servidor com um perfil móvel de usuário para que as informações viajem com o usuário móvel.  
  
  
<a name="quotas"></a>   
## <a name="quotas-for-isolated-storage"></a>Cotas para armazenamento isolado  
 Uma cota é um limite na quantidade de armazenamento isolado que pode ser usada. A cota inclui bytes de espaço de arquivo, bem como a sobrecarga associada ao diretório e outras informações no repositório. O armazenamento isolado usa cotas de permissão, que são limites de armazenamento definidos com o uso de objetos <xref:System.Security.Permissions.IsolatedStoragePermission>. Se você tentar gravar os dados que excedam a cota, uma exceção <xref:System.IO.IsolatedStorage.IsolatedStorageException> será gerada.  Uma política de segurança, a qual pode ser modificada com a .NET Framework Configuration Tool (Mscorcfg.msc), determina quais permissões são concedidas ao código. O código que recebeu <xref:System.Security.Permissions.IsolatedStoragePermission> é restrito a não usar mais armazenamento do que o permitido pela propriedade <xref:System.Security.Permissions.IsolatedStoragePermission.UserQuota%2A>. No entanto, porque o código pode ignorar cotas de permissão ao apresentar identidades de usuário diferentes, as permissões de cotas servem mais como diretrizes de como o código deve se comportar em vez de atuar como um limite firme no comportamento do código.  
  
 As cotas não são aplicadas em repositórios móveis. Devido a isso, um nível um pouco mais alto de permissão é necessário para que o código as use. Os valores de enumeração <xref:System.Security.Permissions.IsolatedStorageContainment.AssemblyIsolationByRoamingUser> e <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByRoamingUser> especificam uma permissão para usar o armazenamento isolado para um usuário móvel.  
  
  
<a name="secure_access"></a>   
## <a name="secure-access"></a>Acesso Seguro  
 Usar o armazenamento isolado permite que aplicativos parcialmente confiáveis armazenem dados de uma maneira que é controlada pela política de segurança do computador. Isto é especialmente útil para componentes baixados que um usuário talvez queira executar com cautela. Uma política de segurança raramente concede esse tipo de permissão de código quando você acessa o sistema de arquivos usando mecanismos padrão de E/S. No entanto, por padrão, código executado do computador local, de uma rede local ou da Internet recebe a permissão para usar o armazenamento isolado.  
  
 Os administradores podem limitar a quantidade de armazenamento isolado que um aplicativo ou usuário tem disponível com base em um nível de confiança apropriado. Além disso, os administradores podem remover todos os dados persistentes de um usuário. Para criar ou acessar um armazenamento isolado, o código deve receber a permissão <xref:System.Security.Permissions.IsolatedStorageFilePermission> apropriada.  
  
 Para acessar um armazenamento isolado, o código deve ter todos os direitos do sistema operacional da plataforma nativa necessários. As listas de controle de acesso (ACLs) que controlam quais usuários têm os direitos necessários para usar o sistema de arquivos devem ser satisfeitas. Os aplicativos .NET Framework já possuem direitos do sistema operacional para acessar armazenamentos isolados, a menos que eles executem a personificação (referente à plataforma). Nesse caso, o aplicativo é responsável por garantir que a identidade do usuário personificado tenha os direitos adequados do sistema operacional para acessar o armazenamento isolado. Esse acesso oferece uma maneira conveniente para que códigos que são executados ou baixados da Web possam ler e gravar em uma área de armazenamento relacionada a um usuário específico.  
  
 Para controlar o acesso ao armazenamento isolado, o Common Language Runtime utiliza objetos <xref:System.Security.Permissions.IsolatedStorageFilePermission>. Cada objeto tem propriedades que especificam os seguintes valores:  
  
-   Utilização permitida, que indica o tipo de acesso que é permitido. Os valores são membros da enumeração <xref:System.Security.Permissions.IsolatedStorageContainment>. Para obter mais informações sobre esses valores, consulte a tabela na próxima seção.  
  
-   Cota de armazenamento, conforme descrito na seção anterior.  
  
 O tempo de execução exige a permissão <xref:System.Security.Permissions.IsolatedStorageFilePermission> quando o código tenta abrir um repositório pela primeira vez. Ele decide se essa permissão será concedida com base em quanto do código é confiável. Se a permissão é concedida, os valores de cota de armazenamento e de utilização permitida são determinados por política de segurança e pela solicitação do código para <xref:System.Security.Permissions.IsolatedStorageFilePermission>. A política de segurança é definida com o auxílio da .NET Framework Configuration Tool (Mscorcfg.msc). Todos os chamadores na pilha de chamadas são verificados para garantir que cada chamador tenha pelo menos a utilização permitida apropriada. O tempo de execução também verifica a cota imposta no código que abriu ou criou o depósito no qual o arquivo será salvo. Se essas condições forem atendidas, a permissão será concedida. A cota é verificada novamente sempre que um arquivo é gravado no repositório.  
  
 O código do aplicativo não é obrigado a solicitar permissão porque o Common Language Runtime concederá qualquer <xref:System.Security.Permissions.IsolatedStorageFilePermission> apropriada com base na política de segurança. No entanto, existem bons motivos para solicitar as permissões específicas de que seu aplicativo necessita, incluindo <xref:System.Security.Permissions.IsolatedStorageFilePermission>.  
  
  
<a name="allowed_usage"></a>   
## <a name="allowed-usage-and-security-risks"></a>Uso permitido e riscos de segurança  
 O uso permitido especificado por <xref:System.Security.Permissions.IsolatedStorageFilePermission> determina o grau ao qual o código terá permissão para criar e usar o armazenamento isolado. A tabela a seguir mostra como o uso permitido especificado na permissão corresponde a tipos de isolamento e resume os riscos de segurança associados a cada uso permitido.  
  
|Uso permitido|Tipos de isolamento|Impacto de segurança|  
|-------------------|---------------------|---------------------|  
|<xref:System.Security.Permissions.IsolatedStorageContainment.None>|Nenhum armazenamento isolado é permitido.|Não há impacto de segurança.|  
|<xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser>|Isolamento por usuário, domínio e assembly Cada assembly possui um sub-repositório separado dentro do domínio. Repositórios que usam essa permissão também são implicitamente isolados por computador.|Esse nível de permissão deixa recursos abertos para superutilização não autorizada, embora cotas impostas tornem isso mais difícil. Isso é denominado um ataque de negação de serviço.|  
|<xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByRoamingUser>|Igual a `DomainIsolationByUser`, mas o armazenamento é salvo em um local que irá transitar se os perfis de usuário móvel estiverem ativados e as cotas não forem aplicadas.|Como as cotas devem ser desativadas, os recursos de armazenamento são mais vulneráveis a um ataque de negação de serviço.|  
|<xref:System.Security.Permissions.IsolatedStorageContainment.AssemblyIsolationByUser>|Isolamento por usuário e assembly Repositórios que usam essa permissão também são implicitamente isolados por computador.|As cotas serão aplicadas nesse nível para ajudar a evitar um ataque de negação de serviço. O mesmo assembly no outro domínio pode acessar esse repositório, abrindo a possibilidade de vazamento de informações entre aplicativos.|  
|<xref:System.Security.Permissions.IsolatedStorageContainment.AssemblyIsolationByRoamingUser>|Igual a `AssemblyIsolationByUser`, mas o armazenamento é salvo em um local que irá transitar se os perfis de usuário móvel estiverem ativados e as cotas não forem aplicadas.|O mesmo que em `AssemblyIsolationByUser`, mas sem as cotas, o risco de um ataque de negação de serviço aumenta.|  
|<xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser>|Isolamento por usuário. Normalmente, apenas ferramentas administrativas ou de depuração usam esse nível de permissão.|O acesso com essa permissão permite que o código exiba ou exclua qualquer um dos arquivos ou diretórios de armazenamento isolados do usuário (independentemente do isolamento do assembly). Riscos incluem, mas não estão limitados a, vazamento de informações e perda de dados.|  
|<xref:System.Security.Permissions.IsolatedStorageContainment.UnrestrictedIsolatedStorage>|Isolamento por todos os usuários, domínios e assemblies. Normalmente, apenas ferramentas administrativas ou de depuração usam esse nível de permissão.|Esta permissão cria o potencial de um comprometimento total de todos os repositórios isolados para todos os usuários.|  
  
  
<a name="isolated_storage_locations"></a>   
## <a name="isolated-storage-locations"></a>Locais de Armazenamento Isolados  
 Às vezes é útil verificar uma alteração em um armazenamento usando o sistema de arquivos do sistema operacional. Talvez você também queira saber o local dos arquivos de armazenamento isolados. Esse local é diferente dependendo do sistema operacional. A tabela a seguir mostra os locais raiz em que um armazenamento isolado é criado em alguns sistemas operacionais comuns. Procure diretórios Microsoft\IsolatedStorage neste local raiz. Você deve alterar as configurações de pasta para mostrar arquivos e pastas ocultos para ver um armazenamento isolado no sistema de arquivos.  
  
|Sistema operacional|Localização no sistema de arquivos|  
|----------------------|-----------------------------|  
|Windows 2000, Windows XP, Windows Server 2003 (atualização do Windows NT 4.0)|Repositórios com suporte a uso móvel =<br /><br /> \<SYSTEMROOT>\Perfis\\<usuário\>\Application Data<br /><br /> Repositórios não móveis =<br /><br /> \<SYSTEMROOT>\Perfis\\<usuário\>\Configurações Locais\Application Data|  
|Windows 2000 – Instalação limpa (e atualizações do Windows 98 e Windows NT 3.51)|Repositórios com suporte a uso móvel =<br /><br /> \<SYSTEMDRIVE>\Documents and Settings\\<usuário\>\Application Data<br /><br /> Repositórios não móveis =<br /><br /> \<SYSTEMDRIVE>\Documents and Settings\\<usuário\>\Configurações Locais\Application Data|  
|Windows XP, Windows Server 2003 – Instalação limpa (e atualizações do Windows 2000 e Windows 98)|Repositórios com suporte a uso móvel =<br /><br /> \<SYSTEMDRIVE>\Documents and Settings\\<usuário\>\Application Data<br /><br /> Repositórios não móveis =<br /><br /> \<SYSTEMDRIVE>\Documents and Settings\\<usuário\>\Configurações Locais\Application Data|  
|[!INCLUDE[win8](../../../includes/win8-md.md)], Windows 7, Windows Server 2008, Windows Vista|Repositórios com suporte a uso móvel =<br /><br /> \<SYSTEMDRIVE>\Users\\<usuário\>\AppData\Roaming<br /><br /> Repositórios não móveis =<br /><br /> \<SYSTEMDRIVE>\Users\\<usuário\>\AppData\Local|  
  
  
<a name="isolated_storage_tasks"></a>   
## <a name="creating-enumerating-and-deleting-isolated-storage"></a>Criando, Enumerando e Excluindo Armazenamento Isolado  
 O .NET Framework fornece três classes no namespace <xref:System.IO.IsolatedStorage> para ajudar a executar as tarefas que envolvem o armazenamento isolado:  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile>, que é derivado de <xref:System.IO.IsolatedStorage.IsolatedStorage?displayProperty=nameWithType> e fornece gerenciamento básico de assemblies armazenados e arquivos de aplicativos. Uma instância da classe <xref:System.IO.IsolatedStorage.IsolatedStorageFile> representa um único repositório localizado no sistema de arquivos.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> deriva de <xref:System.IO.FileStream?displayProperty=nameWithType> e fornece acesso aos arquivos em um repositório.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageScope> é uma enumeração que permite que você crie e selecione um repositório com o tipo de isolamento apropriado.  
  
 As classes de armazenamento isolado permitem que você crie, enumere e exclua o armazenamento isolado. Os métodos para a execução dessas tarefas estão disponíveis através do objeto <xref:System.IO.IsolatedStorage.IsolatedStorageFile>. Algumas operações exigem que você tenha a permissão <xref:System.Security.Permissions.IsolatedStorageFilePermission> que representa o direito para administrar o armazenamento isolado; você também pode precisar ter direitos do sistema operacional para acessar o arquivo ou diretório.  
  
 Para uma série de exemplos que demonstram tarefas de armazenamento isoladas comuns, confira os tópicos listados em [Tópicos relacionados](#related_topics).  
  
  
<a name="scenarios_for_isolated_storage"></a>   
## <a name="scenarios-for-isolated-storage"></a>Cenários para armazenamento isolado  
 O armazenamento isolado é útil em muitas situações, inclusive nestes quatro cenários:  
  
-   Controles baixados. Controles de código gerenciado baixados da Internet não têm permissão para escrever no disco rígido por meio de classes normais de E/S, mas eles podem usar o armazenamento isolado para persistir as configurações do usuário e o estado dos aplicativos.  
  
-   Armazenamento de componentes compartilhado. Componentes que são compartilhados entre aplicativos podem usar o armazenamento isolado para fornecer acesso controlado a repositórios de dados.  
  
-   Armazenamento de servidor. Aplicativos de servidor podem usar o armazenamento isolado para fornecer armazenamento individual para um grande número de usuários que estão realizando solicitações ao aplicativo. Pelo fato do armazenamento isolado ser sempre segredado por usuário, o servidor deve personificar o usuário que fez a solicitação. Nesse caso, os dados são isolados com base na identidade do principal, que é a mesma identidade que o aplicativo usa para fazer a distinção entre os seus usuários.  
  
-   Roaming. Os aplicativos também podem usar o armazenamento isolado com perfis de usuários móveis. Isso permite que repositórios isolados de um usuário façam roaming com o perfil.  
  
 Você não deve usar um armazenamento isolado nas seguintes situações:  
  
-   Para armazenar segredos de alto valor, como chaves sem criptografia ou senhas, pois o armazenamento isolado não é protegido contra código altamente confiável, código não gerenciado ou usuários confiáveis do computador.  
  
-   Para armazenar código.  
  
-   Para armazenar configurações e opções de implantação, as quais são controladas pelos administradores. (As preferências do usuário não são consideradas como definições de configuração, pois os administradores não as controlam.)  
  
 Muitos aplicativos usam bancos de dados para armazenar e isolar os dados. Nesse caso uma ou mais linhas em um banco de dados podem representar o armazenamento para um usuário específico. Você pode optar por usar armazenamento isolado em vez de um banco de dados quando o número de usuários é pequeno, quando as despesas no uso de um banco de dados é significativa ou quando não existe nenhum recurso de banco de dados. Além disso, quando o aplicativo requer um armazenamento que seja mais flexível e complexo do que aquele fornecido por uma linha em um banco de dados, o armazenamento isolado pode fornecer uma alternativa viável.  
  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Tipos de isolamento](../../../docs/standard/io/types-of-isolation.md)|Descreve os diferentes tipos de isolamento.|  
|[Como obter repositórios para o armazenamento isolado](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)|Fornece um exemplo de uso da classe <xref:System.IO.IsolatedStorage.IsolatedStorageFile> para obter um armazenamento isolado por usuário e assembly.|  
|[Como enumerar repositórios para o armazenamento isolado](../../../docs/standard/io/how-to-enumerate-stores-for-isolated-storage.md)|Mostra como usar o método <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> para calcular o tamanho de todo o armazenamento isolado para o usuário.|  
|[Como excluir repositórios no armazenamento isolado](../../../docs/standard/io/how-to-delete-stores-in-isolated-storage.md)|Mostra como usar o método <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A?displayProperty=nameWithType> de duas maneiras diferentes para excluir repositórios isolados.|  
|[Como prever condições de espaço insuficiente com o armazenamento isolado](../../../docs/standard/io/how-to-anticipate-out-of-space-conditions-with-isolated-storage.md)|Mostra como a medir o espaço restante em um armazenamento isolado.|  
|[Como criar arquivos e diretórios no armazenamento isolado](../../../docs/standard/io/how-to-create-files-and-directories-in-isolated-storage.md)|Fornece alguns exemplos de criação de arquivos e diretórios em um repositório isolado.|  
|[Como localizar arquivos e diretórios existentes no armazenamento isolado](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)|Demonstra como ler a estrutura de diretórios e arquivos no armazenamento isolado.|  
|[Como ler e gravar em arquivos no armazenamento isolado](../../../docs/standard/io/how-to-read-and-write-to-files-in-isolated-storage.md)|Fornece um exemplo de gravação de uma cadeia de caracteres em um arquivo de armazenamento isolado, seguida por sua leitura de volta.|  
|[Como excluir arquivos e diretórios no armazenamento isolado](../../../docs/standard/io/how-to-delete-files-and-directories-in-isolated-storage.md)|Demonstra como excluir arquivos e diretórios isolados.|  
|[E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)|Explica como você pode executar acesso síncrono e assíncrono a fluxos de dados e arquivos.|  
  
<a name="reference"></a>   
## <a name="reference"></a>Referência  
 <xref:System.IO.IsolatedStorage.IsolatedStorage?displayProperty=nameWithType>  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream?displayProperty=nameWithType>  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope?displayProperty=nameWithType>
