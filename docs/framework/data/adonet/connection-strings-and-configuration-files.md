---
title: Cadeias de conexão e arquivos de configuração
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 37df2641-661e-407a-a3fb-7bf9540f01e8
ms.openlocfilehash: a4876d3b794282852b364f58cc84b58546567d80
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="connection-strings-and-configuration-files"></a>Cadeias de conexão e arquivos de configuração
Inserir cadeias de conexão no código do seu aplicativo pode resultar em vulnerabilidades de segurança e problemas de manutenção. Cadeias de caracteres de conexão não criptografada compiladas em código-fonte do aplicativo podem ser exibidas usando o [Ildasm.exe (IL Disassembler)](../../../../docs/framework/tools/ildasm-exe-il-disassembler.md) ferramenta. Além disso, se a cadeia de conexão for alterada, seu aplicativo deverá ser recompilado. Por esses motivos, recomendamos armazenar cadeias de conexão em um arquivo de configuração do aplicativo.  
  
## <a name="working-with-application-configuration-files"></a>Trabalhando com arquivos de configuração de aplicativo  
 Os arquivos de configuração do aplicativo contêm as configurações que são específicas para um determinado aplicativo. Por exemplo, um aplicativo ASP.NET pode ter um ou mais **Web. config** arquivos e um aplicativo do Windows podem ter um opcional **App. config** arquivo. Os arquivos de configuração compartilham elementos comuns, embora o nome e o local de um arquivo de configuração variem dependendo do host do aplicativo.  
  
### <a name="the-connectionstrings-section"></a>A seção de connectionStrings  
 Cadeias de caracteres de Conexão podem ser armazenadas como pares chave/valor no **connectionStrings** seção o **configuração** elemento de um arquivo de configuração do aplicativo. Elementos filho incluem **adicionar**, **limpar**, e **remover**.  
  
 O fragmento de arquivo de configuração a seguir demonstra o esquema e a sintaxe para armazenar uma cadeia de conexão. O **nome** atributo é um nome que você fornecer para identificar exclusivamente uma cadeia de caracteres de conexão para que ele possa ser recuperado em tempo de execução. O **providerName** é o nome invariável do provedor de dados do .NET Framework, que é registrado no arquivo Machine. config.  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
  <configuration>  
    <connectionStrings>  
      <clear />  
      <add name="Name"   
       providerName="System.Data.ProviderName"   
       connectionString="Valid Connection String;" />  
    </connectionStrings>  
  </configuration>  
```  
  
> [!NOTE]
>  Você pode salvar parte de uma cadeia de conexão em um arquivo de configuração e usar a classe <xref:System.Data.Common.DbConnectionStringBuilder> para concluí-la em tempo de execução. Isso é útil em situações onde você não conhece os elementos da cadeia de conexão com antecedência, ou quando não quer salvar informações confidenciais em um arquivo de configuração. Para obter mais informações, consulte [construtores de cadeia de Conexão](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
### <a name="using-external-configuration-files"></a>Utilizando arquivos de configuração externos  
 Os arquivos de configuração externos são arquivos separados que contêm um fragmento de um arquivo de configuração que consiste em uma única seção. O arquivo de configuração externo é, em seguida, referenciado pelo arquivo de configuração principal. Armazenar o **connectionStrings** seção em um arquivo fisicamente separado é útil em situações em que as cadeias de caracteres de conexão podem ser editadas depois que o aplicativo é implantado. Por exemplo, o comportamento padrão do ASP.NET é reiniciar o domínio de um aplicativo quando os arquivos de configuração são modificados, o que resulta em perda de informações de estado. No entanto, modificar um arquivo de configuração externo não causa uma reinicialização do aplicativo. Os arquivos de configuração externos não estão limitados ao ASP.NET; eles também podem ser usados por aplicativos do Windows. Além disso, a segurança de acesso a arquivos e as permissões podem ser usadas para restringir o acesso a arquivos de configuração externos. Trabalhar com arquivos de configuração externos em tempo de execução é transparente e não exige nenhuma codificação especial.  
  
 Para armazenar cadeias de caracteres de conexão no arquivo de configuração externo, crie um arquivo separado que contém apenas o **connectionStrings** seção. Não inclui elementos, seções ou atributos adicionais. Este exemplo mostra a sintaxe para um arquivo de configuração externo.  
  
```xml  
<connectionStrings>  
  <add name="Name"   
   providerName="System.Data.ProviderName"   
   connectionString="Valid Connection String;" />  
</connectionStrings>  
```  
  
 No arquivo de configuração do aplicativo principal, você deve usar o **configSource** atributo para especificar o nome totalmente qualificado e o local do arquivo externo. Este exemplo refere-se a um arquivo de configuração externo chamado `connections.config`.  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
<configuration>  
    <connectionStrings configSource="connections.config"/>  
</configuration>  
```  
  
## <a name="retrieving-connection-strings-at-run-time"></a>Recuperando cadeias de conexão em tempo de execução  
 O .NET Framework 2.0 introduziu novas classes no namespace <xref:System.Configuration> para simplificar a recuperação de cadeias de conexão de arquivos de configuração em tempo de execução. Você pode programaticamente recuperar uma cadeia de conexão por nome ou nome do provedor.  
  
> [!NOTE]
>  O **Machine. config** arquivo também contém um **connectionStrings** seção, que contém as cadeias de conexão usadas pelo Visual Studio. Ao recuperar cadeias de caracteres de conexão por nome do provedor do **App. config** arquivo em um aplicativo do Windows, as cadeias de conexão **Machine. config** obter carregado primeiro e, em seguida, as entradas de **App. config**. Adicionando **limpar** imediatamente após o **connectionStrings** elemento remove herdadas todas as referências a estrutura de dados na memória, para que apenas as cadeias de caracteres de conexão definidas no local **App. config** arquivo são considerados.  
  
### <a name="working-with-the-configuration-classes"></a>Trabalhando com as classes de configuração  
 A partir do .NET Framework 2.0, <xref:System.Configuration.ConfigurationManager> é usado ao trabalhar com arquivos de configuração no computador local, substituindo o <xref:System.Configuration.ConfigurationSettings> obsoleto. <xref:System.Web.Configuration.WebConfigurationManager> é usado para trabalhar com arquivos de configuração do ASP.NET. Ele foi projetado para trabalhar com arquivos de configuração em um servidor Web e permite o acesso programático a seções do arquivo de configuração como **System. Web**.  
  
> [!NOTE]
>  Acessar arquivos de configuração em tempo de execução exige a concessão de permissões para o chamador; as permissões necessárias dependem do tipo de aplicativo, do arquivo de configuração e do local. Para obter mais informações, consulte [usando as Classes de configuração](http://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc) e <xref:System.Web.Configuration.WebConfigurationManager> para aplicativos ASP.NET, e <xref:System.Configuration.ConfigurationManager> para aplicativos do Windows.  
  
 Você pode usar <xref:System.Configuration.ConnectionStringSettingsCollection> para recuperar cadeias de conexão de arquivos de configuração do aplicativo. Ele contém uma coleção de <xref:System.Configuration.ConnectionStringSettings> objetos, cada um deles representa uma única entrada no **connectionStrings** seção. Suas propriedades mapeiam para atributos de cadeia de conexão, permitindo que você recupere uma cadeia de conexão especificando o nome ou o nome do provedor.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|<xref:System.Configuration.ConnectionStringSettings.Name%2A>|O nome da cadeia de conexão. Mapeia para o **nome** atributo.|  
|<xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>|O nome do provedor totalmente qualificado. Mapeia para o **providerName** atributo.|  
|<xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>|A cadeia de conexão. Mapeia para o **connectionString** atributo.|  
  
### <a name="example-listing-all-connection-strings"></a>Exemplo: listando todas as cadeias de conexão  
 Este exemplo itera por meio da coleção de `ConnectionStringSettings` e exibe as propriedades <xref:System.Configuration.ConnectionStringSettings.Name%2A>, <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> e <xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A> na janela do console.  
  
> [!NOTE]
>  System.Configuration.dll não está incluído em todos os tipos de projeto, e você talvez precise definir uma referência para ele para usar as classes de configuração. O nome e o local de um arquivo de configuração do aplicativo específico variam pelo tipo de aplicativo e o processo de hospedagem.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-name"></a>Exemplo: recuperando uma cadeia de conexão por nome  
 Este exemplo demonstra como recuperar uma cadeia de conexão de um arquivo de configuração especificando seu nome. O código cria um objeto <xref:System.Configuration.ConnectionStringSettings>, correspondendo o parâmetro de entrada fornecido com o nome de <xref:System.Configuration.ConfigurationManager.ConnectionStrings%2A>. Se nenhum nome correspondente for localizado, a função retornará `null` (`Nothing` no Visual Basic).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-provider-name"></a>Exemplo: recuperando uma cadeia de conexão por nome de provedor  
 Este exemplo demonstra como recuperar uma cadeia de caracteres de conexão, especificando o nome invariável do provedor no formato *System.Data.ProviderName*. O código itera por meio do <xref:System.Configuration.ConnectionStringSettingsCollection> e retorna a cadeia de conexão para o primeiro <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> encontrado. Se o nome do provedor não for localizado, a função retornará `null` (`Nothing` no Visual Basic).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="encrypting-configuration-file-sections-using-protected-configuration"></a>Criptografando seções do arquivo de configuração usando configuração protegida  
 O ASP.NET 2.0 introduziu um novo recurso chamado *configuração protegida*, que permite que você criptografe as informações confidenciais em um arquivo de configuração. Embora tenha sido projetado principalmente para ASP.NET, a configuração protegida também pode ser usada para criptografar seções do arquivo de configuração em aplicativos do Windows. Para obter uma descrição detalhada dos recursos de configuração protegida, consulte [Criptografando informações de configuração usando configuração protegida](http://msdn.microsoft.com/library/51cdfe5b-9d82-458c-94ff-c551c4f38ed1).  
  
 O arquivo de configuração a seguir fragmento mostra o **connectionStrings** seção depois que ele foi criptografado. O **configProtectionProvider** Especifica o provedor de configuração protegida usado para criptografar e descriptografar as cadeias de caracteres de conexão. O **EncryptedData** seção contém o texto cifrado.  
  
```xml  
<connectionStrings configProtectionProvider="DataProtectionConfigurationProvider">  
  <EncryptedData>  
    <CipherData>  
      <CipherValue>AQAAANCMnd8BFdERjHoAwE/Cl+sBAAAAH2... </CipherValue>  
    </CipherData>  
  </EncryptedData>  
</connectionStrings>  
```  
  
 Quando a cadeia de caracteres de conexão criptografada é recuperada em tempo de execução, o .NET Framework usa o provedor especificado para descriptografar o **CipherValue** e disponibilizá-la para seu aplicativo. Você não precisa escrever nenhum código adicional para gerenciar o processo descriptografia.  
  
### <a name="protected-configuration-providers"></a>Provedores de configuração protegida  
 Provedores de configuração protegida são registrados no **configProtectedData** seção o **Machine. config** de arquivo no computador local, conforme mostrado no fragmento a seguir, que mostra os dois provedores de configuração protegida fornecidos com o .NET Framework. Os valores mostrados aqui foram truncados para facilitar a leitura.  
  
```xml  
<configProtectedData defaultProvider="RsaProtectedConfigurationProvider">  
  <providers>  
    <add name="RsaProtectedConfigurationProvider"   
      type="System.Configuration.RsaProtectedConfigurationProvider, ... />  
    <add name="DataProtectionConfigurationProvider"   
      type="System.Configuration.DpapiProtectedConfigurationProvider, ... />  
  </providers>  
</configProtectedData>  
```  
  
 Você pode configurar os provedores de configuração protegida adicionais ao adicioná-los para o **Machine. config** arquivo. Você também pode criar seu próprio provedor de configuração protegida por herança da classe base abstrata <xref:System.Configuration.ProtectedConfigurationProvider>. A tabela a seguir descreve os dois arquivos de configuração incluídos no .NET Framework.  
  
|Provider|Descrição|  
|--------------|-----------------|  
|<!--zz<xref:System.Configuration.RSAProtectedConfigurationProvider>-->`System.Configuration.RSAProtectedConfigurationProvider`|Usa o algoritmo de criptografia RSA para criptografar e descriptografar dados. O algoritmo RSA pode ser usado para criptografia de chave pública e assinaturas digitais. Também é conhecido como “chave pública” ou criptografia assimétrica porque emprega duas chaves diferentes. Você pode usar o [ferramenta de registro ASP.NET IIS (Aspnet_regiis.exe)](http://msdn.microsoft.com/library/6491c41e-e2b0-481f-9863-db3614d5f96b) para criptografar as seções de um arquivo Web. config e gerenciar as chaves de criptografia. O ASP.NET descriptografa o arquivo de configuração quando processa o arquivo. A identidade do aplicativo do ASP.NET deve ter acesso de leitura para a chave de criptografia que é usada para criptografar e descriptografar as seções criptografadas.|  
|<!--zz<xref:System.Configuration.DPAPIProtectedConfigurationProvider>-->`System.Configuration.DPAPIProtectedConfigurationProvider`|Usa a API de Proteção aos Dados do Windows (DPAPI) para criptografar seções de configuração. Usa os serviços de criptografia internos do Windows e pode ser configurado para proteção específica de computador ou da conta do usuário. A proteção específica do computador é útil para vários aplicativos no mesmo servidor que precisam compartilhar informações. A proteção específica da conta do usuário pode ser usada com serviços que são executados com uma identidade de usuário específica, como um ambiente de hospedagem compartilhado. Cada aplicativo é executado em uma identidade separada que restringe o acesso a recursos como arquivos e bancos de dados.|  
  
 Os dois provedores oferecem criptografia de dados forte. Entretanto, se você estiver planejando usar o mesmo arquivo de configuração criptografado em vários servidores, como uma Web farm, apenas o `RsaProtectedConfigurationProvider` permite que você exporte as chaves de criptografia usadas para criptografar os dados e importá-los em outro servidor. Para obter mais informações, consulte [importando e exportando Protected Configuration RSA Key Containers](http://msdn.microsoft.com/library/f3022b39-f17f-48c1-b067-025eab0ce8bc).  
  
### <a name="using-the-configuration-classes"></a>Usando as classes de configuração  
 O namespace <xref:System.Configuration> fornece classes para trabalhar com parâmetros de configuração programaticamente. A classe <xref:System.Configuration.ConfigurationManager> fornece acesso a arquivos de computador, aplicativo e configuração do usuário. Se você estiver criando um aplicativo ASP.NET, você pode usar o <xref:System.Web.Configuration.WebConfigurationManager> classe, que fornece a mesma funcionalidade, enquanto também permitindo que você acesse as configurações que são exclusivas para aplicativos ASP.NET, como aqueles encontrados no  **\< System. Web >**.  
  
> [!NOTE]
>  O namespace <xref:System.Security.Cryptography> contém classes que oferecem opções adicionais para criptografar e descriptografar dados. Use essas classes se você precisar de serviços de criptografia que não estão disponíveis usando a configuração protegida. Algumas dessas classes são wrappers da Microsoft CryptoAPI não gerenciada, enquanto outras são implementações puramente gerenciadas. Para obter mais informações, consulte [Serviços Criptográficos](http://msdn.microsoft.com/library/68a1e844-c63c-44af-9247-f6716eb23781).  
  
### <a name="appconfig-example"></a>Exemplo de App.config  
 Este exemplo demonstra como ativar a criptografia de **connectionStrings** seção um **App. config** arquivo para um aplicativo do Windows. Nesse exemplo, o procedimento utiliza o nome do aplicativo como um argumento, por exemplo, “MyApplication.exe”. O **App. config** arquivo, em seguida, será criptografado e copiado para a pasta que contém o executável com o nome de "MyApplication.exe.config".  
  
> [!NOTE]
>  A cadeia de conexão somente pode ser descriptografada no computador no qual foi criptografada.  
  
 O código usa o <xref:System.Configuration.ConfigurationManager.OpenExeConfiguration%2A> método para abrir o **App. config** arquivo para edição e o <xref:System.Configuration.ConfigurationManager.GetSection%2A> método retorna o **connectionStrings** seção. O código em seguida verifica a propriedade <xref:System.Configuration.SectionInformation.IsProtected%2A>, chamando <xref:System.Configuration.SectionInformation.ProtectSection%2A> para criptografar a seção se não estiver criptografada. O método <xref:System.Configuration.SectionInformation.UnprotectSection%2A> é chamado para descriptografar a seção. O método <xref:System.Configuration.Configuration.Save%2A> conclui a operação e salva as alterações.  
  
> [!NOTE]
>  Você deve definir uma referência a `System.Configuration.dll` em seu projeto para que o código seja executado.  
  
 [!code-csharp[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/VB/source.vb#1)]  
  
### <a name="webconfig-example"></a>Exemplo de Web.config  
 Esse exemplo usa o método <xref:System.Web.Configuration.WebConfigurationManager.OpenWebConfiguration%2A> do `WebConfigurationManager`. Observe que neste caso você pode fornecer o caminho relativo para o **Web. config** arquivo usando um til. O código exige uma referência à classe `System.Web.Configuration`.  
  
 [!code-csharp[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/VB/source.vb#1)]  
  
 Para obter mais informações para proteger aplicativos ASP.NET, consulte [NIB: segurança ASP.NET](http://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d) e [práticas de segurança do ASP.NET 2.0 em um relance](http://go.microsoft.com/fwlink/?LinkId=59997) no Centro de desenvolvedores do ASP.NET.  
  
## <a name="see-also"></a>Consulte também  
 [Construtores de cadeia de Conexão](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [Usando as Classes de configuração](http://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc)  
 [Configurando aplicativos](../../../../docs/framework/configure-apps/index.md)  
 [Administração de Site da Web do ASP.NET](http://msdn.microsoft.com/library/1298034b-5f7d-464d-abd1-ad9e6b3eeb7e)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
