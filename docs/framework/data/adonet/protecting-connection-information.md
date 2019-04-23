---
title: Protegendo informações de conexão
ms.date: 03/30/2017
ms.assetid: 1471f580-bcd4-4046-bdaf-d2541ecda2f4
ms.openlocfilehash: ccb039a79c76c31b905783b81710571d8c5ab82b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184438"
---
# <a name="protecting-connection-information"></a>Protegendo informações de conexão
A proteção do acesso à fonte de dados é essencial para a segurança do aplicativo. Uma cadeia de conexão apresenta uma vulnerabilidade potencial se não estiver protegida. Armazenar as informações de conexão em texto sem formatação ou persistir-la na memória pode comprometer seu sistema inteiro. Cadeias de caracteres de Conexão inseridas no seu código-fonte podem ser lido usando o [Ildasm.exe (IL Disassembler)](../../../../docs/framework/tools/ildasm-exe-il-disassembler.md) para exibir o Microsoft intermediate language (MSIL) em um assembly compilado.  
  
 As vulnerabilidades de segurança envolvendo cadeias de conexão podem surgir com base no tipo de autenticação usado, em como as cadeias de conexão são persistidas na memória e no disco e nas técnicas usadas para construí-los em tempo de execução.  
  
## <a name="use-windows-authentication"></a>Use a Autenticação do Windows  
 Para ajudar a limitar o acesso a sua fonte de dados, você deverá proteger as informações de conexão como a identificação do usuário, senha e nome da fonte de dados. Para evitar expor as informações do usuário, é recomendável usar a autenticação do Windows (também conhecido como *a segurança integrada*) sempre que possível. A autenticação do Windows é especificada em uma cadeia de conexão usando as palavras-chave `Integrated Security` ou `Trusted_Connection`, eliminando a necessidade de usar uma identificação de usuário e senha. Ao usar a autenticação do Windows, os usuários são autenticados pelo Windows e o acesso ao servidor e os recursos de banco de dados são determinados concedendo permissões a usuários e grupos do Windows.  
  
 Para situações onde não é possível usar a autenticação do Windows, você deverá ter cuidado adicional porque as credenciais do usuário são expostas na cadeia de conexão. Em um aplicativo do ASP.NET, você pode configurar uma conta do Windows como uma identidade fixa que é usada para se conectar a bancos de dados e outros recursos de rede. Habilitar a representação no elemento identity na **Web. config** de arquivo e especifique um nome de usuário e senha.  
  
```xml  
<identity impersonate="true"   
        userName="MyDomain\UserAccount"   
        password="*****" />  
```  
  
 A conta de identidade fixa deve ser uma conta de privilégios baixos que tem concedidas somente as permissões necessárias no banco de dados. Além disso, você deve criptografar o arquivo de configuração de modo que o nome de usuário e a senha não sejam expostos em texto não criptografado.  
  
## <a name="do-not-use-universal-data-link-udl-files"></a>Não use arquivos UDL (Universal Data Link)  
 Evite armazenar cadeias de conexão para um <xref:System.Data.OleDb.OleDbConnection> em um arquivo UDL (Universal Data Link). UDLs são armazenados em texto não criptografado e não podem ser criptografados. Um arquivo UDL é um recurso externo com base em arquivo para o seu aplicativo e ele não poderá ser protegido ou criptografado usando o .NET Framework.  
  
## <a name="avoid-injection-attacks-with-connection-string-builders"></a>Evite ataques de injeção com construtores de cadeia de conexão  
 Um ataque de injeção de cadeia de conexão pode ocorrer quando a concatenação dinâmica de cadeia de caracteres é usada para criar cadeias de conexão com base na entrada do usuário. Se a entrada do usuário não for validada e o texto mal-intencionado ou caracteres não forem escapados, um invasor poderá acessar dados confidenciais ou outros recursos no servidor. Para resolver esse problema, o ADO.NET 2.0 introduziu novas classes de construtor de cadeia de conexão para validar a sintaxe da cadeia de conexão e garantir que os parâmetros adicionais não sejam introduzidos. Para obter mais informações, confira [Construtores de cadeias de conexão](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
## <a name="use-persist-security-infofalse"></a>Use segurança de persistência Info=False  
 O valor padrão para `Persist Security Info` é falso; nós recomendamos usar esta opção em todas as cadeias de conexão. Configurar `Persist Security Info` como `true` ou `yes` permite informações confidenciais de segurança, incluindo a identificação de usuário e a senha, para serem obtidas de uma conexão depois que ela tiver sido aberta. Quando `Persist Security Info` for definido como `false` ou `no`, as informações de segurança serão descartadas após serem usadas para abrir a conexão, garantindo que uma fonte não confiável não tenha acesso a informações confidenciais de segurança.  
  
## <a name="encrypt-configuration-files"></a>Criptografe arquivos de configuração  
 Você também pode armazenar cadeias de conexão em arquivos de configuração, o que elimina a necessidade de inseri-las no código do aplicativo. Os arquivos de configuração são arquivos XML padrão para os quais o .NET Framework definiu um conjunto comum de elementos. Cadeias de caracteres de Conexão em arquivos de configuração são geralmente armazenadas dentro de  **\<connectionStrings >** elemento no **App. config** para um aplicativo do Windows, ou o  **Web. config** arquivo para um aplicativo ASP.NET. Para obter mais informações sobre os conceitos básicos de armazenamento, recuperação e criptografia de cadeias de caracteres de conexão de arquivos de configuração, consulte [cadeias de caracteres de Conexão e arquivos de configuração](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).  
  
## <a name="see-also"></a>Consulte também

- [Securing ADO.NET Applications](../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)
- [Criptografando informações de configuração usando configuração protegida](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100))
- [Segurança no .NET](../../../standard/security/index.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
