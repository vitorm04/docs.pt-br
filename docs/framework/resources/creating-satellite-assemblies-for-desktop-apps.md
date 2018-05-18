---
title: Criando assemblies satélite para aplicativos de área de trabalho
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- hub-and-spoke resource deployment model
- resource files, packaging
- application resources, packaging
- public keys, obtaining
- satellite assemblies
- assemblies [.NET Framework], signing
- application resources, deploying
- Al.exe
- GAC (global assembly cache), satellite assemblies
- Assembly Linker
- directory locations for satellite assemblies
- global assembly cache, satellite assemblies
- packaging application resources
- compiling satellite assemblies
- re-signing assemblies
ms.assetid: 8d5c6044-2919-41d2-8321-274706b295ac
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c308c7e16f106d00e5fd1b5ad820f8b330f4bbbf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="creating-satellite-assemblies-for-desktop-apps"></a>Criando assemblies satélite para aplicativos de área de trabalho
Arquivos de recurso desempenham um papel central em aplicativos localizados. Eles permitem que um aplicativo exiba cadeias de caracteres, imagens e outros dados no idioma e na cultura do usuário e forneça dados alternativos se esses recursos não estiverem disponíveis. O .NET Framework usa um modelo de hub e spoke para localizar e recuperar os recursos localizados. O hub é o principal assembly que contém o código executável não localizável e os recursos para uma única cultura, que é chamada de cultura neutra ou padrão. O padrão é a cultura de fallback para o aplicativo; ela é usada quando não há recursos localizados disponíveis. Você usa o atributo <xref:System.Resources.NeutralResourcesLanguageAttribute> para designar a cultura da cultura padrão do aplicativo. Cada spoke conecta-se a um assembly satélite que contém os recursos para uma única cultura localizada, mas não contém nenhum código. Como os assemblies satélite não fazem parte do assembly principal, você pode facilmente atualizar ou substituir recursos que correspondem a uma cultura específica sem substituir o assembly principal do aplicativo.  
  
> [!NOTE]
>  Os recursos da cultura padrão de um aplicativo também podem ser armazenados em um assembly satélite. Para fazer isso, você atribui ao atributo <xref:System.Resources.NeutralResourcesLanguageAttribute> um valor de <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType>.  
  
## <a name="satellite-assembly-name-and-location"></a>Nome e local do assembly satélite  
 Esse modelo hub e spoke requer que você coloque recursos em locais específicos, para que possam ser facilmente localizados e usados. Se você não compilar e nomear os recursos conforme esperado, ou se não colocá-los nos locais corretos, o CLR não poderá localizá-los e usará os recursos da cultura padrão. O Gerenciador de Recursos do .NET Framework, representado por um objeto <xref:System.Resources.ResourceManager>, é usado para acessar automaticamente os recursos localizados. O Gerenciador de Recursos requer o seguinte:  
  
-   Um assembly satélite único deve incluir todos os recursos de uma cultura específica. Em outras palavras, você deve compilar vários arquivos .txt ou .resx em um arquivo binário .resources.  
  
-   Deve haver um subdiretório separado no diretório do aplicativo para cada cultura localizada que armazena os recursos da cultura. O nome do subdiretório deve ser igual ao nome de cultura. Como alternativa, você pode armazenar seus assemblies satélites no cache de assembly global. Nesse caso, o componente de informações de cultura do nome forte do assembly deve indicar sua cultura. (Consulte a seção [Instalação dos assemblies de satélite no cache de assembly global](#SN), mais adiante neste tópico.)  
  
    > [!NOTE]
    >  Se o aplicativo incluir recursos para subculturas, coloque cada subcultura em um subdiretório separado no diretório do aplicativo. Não coloque subculturas em subdiretórios no diretório principal da sua cultura.  
  
-   O assembly satélite deve ter o mesmo nome que o aplicativo e usar a extensão de nome de arquivo ".resources.dll". Por exemplo, se um aplicativo for denominado Example.exe, o nome de cada assembly satélite deverá ser Example.resources.dll. Observe que o nome do assembly satélite não indica a cultura dos seus arquivos de recursos. No entanto, o assembly satélite aparece em um diretório que especifica a cultura.  
  
-   Informações sobre a cultura do assembly satélite devem ser incluídas nos metadados do assembly. Para armazenar o nome da cultura nos metadados do assembly satélite, você deve especificar a opção `/culture` quando usar o [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md) para incorporar recursos no assembly satélite.  
  
 A ilustração a seguir mostra a estrutura e os requisitos de localização de um diretório de exemplo para os aplicativos que você não está instalando no [cache de assembly global](../../../docs/framework/app-domains/gac.md). Os itens com as extensões .txt e .resources não serão fornecidos com o aplicativo final. Esses são os arquivos de recurso intermediários usados para criar os assemblies satélite finais de recursos. Neste exemplo, você poderia substituir arquivos .resx por arquivos .txt. Para obter mais informações, consulte [Empacotamento e implantação de recursos](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).  
  
 ![Assemblies satélite](../../../docs/framework/resources/media/satelliteassemblydir.gif "satelliteassemblydir")  
Diretório do assembly satélite  
  
## <a name="compiling-satellite-assemblies"></a>Compilação de assemblies satélite  
 Você usa o [Gerador de arquivos de recurso (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) para compilar arquivos de texto ou XML (.resx) que contenham arquivos binários .resources. Em seguida, usa o [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) para compilar arquivos .resources em assemblies satélite. O Al.exe cria um conjunto de arquivos usando o .resources que você especificar. Assemblies satélites podem conter somente recursos; eles não podem conter nenhum código executável.  
  
 O comando a seguir Al.exe cria um assembly satélite para o aplicativo `Example` usando o arquivo de recursos alemão strings.de.resources.  
  
```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll  
```  
  
 O comando a seguir Al.exe cria um assembly satélite para o aplicativo `Example` usando o arquivo strings.de.resources. A opção **/template** faz com que o assembly satélite herde todos os metadados de assembly, exceto as informações de cultura do assembly pai (Example. dll).  
  
```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll -template:Example.dll  
```  
  
 A tabela a seguir descreve em detalhes as opções de Al.exe usadas nesses comandos.  
  
|Opção|Descrição|  
|------------|-----------------|  
|**-target:** lib|Especifica que o seu assembly satélite é compilado em um arquivo de biblioteca (. dll). Como um assembly satélite não contém código executável e não é um assembly principal do aplicativo, você deve salvar assemblies satélites como DLLs.|  
|**-embed:** strings.de.resources|Especifica o nome do arquivo de recurso incorporado quando o Al.exe compila o assembly. Você pode incorporar vários arquivos .resources em um assembly satélite, mas se estiver seguindo o modelo hub e spoke, compile um assembly satélite para cada cultura. No entanto, você pode criar arquivos .resources separados para cadeias de caracteres e objetos.|  
|**-culture:** de|Especifica a cultura do recurso para compilar. O Common Language Runtime usa essas informações ao procurar os recursos de uma cultura específica. Se você omitir esta opção, o Al.exe ainda compilará o recurso, mas o tempo de execução não será capaz de localizá-lo quando um usuário solicitá-lo.|  
|**-out:** Example.resources.dll|Especifica o nome do arquivo de saída. O nome deve seguir o padrão de nomeação *baseName*.resources. *extensão*, onde *baseName* é o nome do assembly principal, e *extension* é uma extensão de nome de arquivo válido (como .dll). Observe que o tempo de execução não é capaz de determinar a cultura de um assembly satélite com base em seu nome de arquivo de saída; você deve usar a opção **/culture** para especificá-lo.|  
|**-template:** Example.dll|Especifica o assembly do qual todos os metadados de assembly devem ser herdados, exceto o campo de cultura. Esta opção afetará assemblies satélites somente se você especificar um assembly com um [nome forte](../../../docs/framework/app-domains/strong-named-assemblies.md).|  
  
 Para obter uma lista completa das opções disponíveis com Al.exe, consulte [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
## <a name="satellite-assemblies-an-example"></a>Assemblies satélites: um exemplo  
 Este é um exemplo simples "Olá, Mundo", que exibe uma caixa de mensagem com uma saudação localizada. O exemplo inclui recursos para as culturas inglesas (Estados Unidos), francesas (França) e russas (Rússia), e sua cultura de fallback é o inglês. Para criar o exemplo, faça o seguinte:  
  
1.  Crie um arquivo de recurso chamado Greeting.resx ou Greeting.txt para conter o recurso para a cultura padrão. Armazene uma única cadeia de caracteres denominada `HelloString`, cujo valor é "Hello world!" neste arquivo.  
  
2.  Para indicar que inglês (en) é a cultura padrão do aplicativo, adicione o seguinte atributo <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> ao arquivo AssemblyInfo do aplicativo ou ao arquivo de código-fonte principal que será compilado no assembly principal do aplicativo.  
  
     [!code-csharp[Conceptual.Resources.Locating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/assemblyinfo.cs#2)]
     [!code-vb[Conceptual.Resources.Locating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/assemblyinfo.vb#2)]  
  
3.  Adicione suporte a culturas adicionais (en-US, fr-FR e ru-RU) ao aplicativo da seguinte maneira:  
  
    -   Para oferecer suporte à cultura inglesa (Estados Unidos) ou en-US, crie um arquivo de recurso chamado Greeting.en-US.resx ou Greeting.en- US.txt e armazene nele uma única cadeia de caracteres denominada `HelloString`, cujo valor é "Hi world!"  
  
    -   Para oferecer suporte à cultura francesa (França) ou fr-FR, crie um arquivo de recurso chamado Greeting.fr-FR.resx ou Greeting.fr-FR.txt e armazene nele uma única cadeia de caracteres denominada `HelloString`, cujo valor é "Salout tout le monde!"  
  
    -   Para oferecer suporte à cultura russa (Rússia) ou ru-RU, crie um arquivo de recurso chamado Greeting.ru-RU.resx ou Greeting.ru-RU.txt e armazene nele uma única cadeia de caracteres denominada `HelloString`, cujo valor é "Всем привет!"  
  
4.  Use [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) para compilar cada texto ou um arquivo de recursos XML em um arquivo binário .resources. A saída é um conjunto de arquivos que têm o mesmo nome de arquivo raiz que os arquivos. resx ou. txt, mas uma extensão .resources. Se você criar o exemplo com o Visual Studio, o processo de compilação será manipulado automaticamente. Se você não estiver usando o Visual Studio, execute os seguintes comandos para compilar os arquivos .resx em arquivos .resources:  
  
    ```console
    resgen Greeting.resx  
    resgen Greeting.en-us.resx  
    resgen Greeting.fr-FR.resx  
    resgen Greeting.ru-RU.resx  
    ```  
  
     Se os recursos estiverem em arquivos de texto em vez de arquivos XML, substitua a extensão .resx por .txt.  
  
5.  Compile o código-fonte abaixo com os recursos para a cultura padrão no assembly principal do aplicativo:  
  
    > [!IMPORTANT]
    >  Se você estiver usando a linha de comando em vez do Visual Studio para criar o exemplo, deverá modificar a chamada para o construtor de classe <xref:System.Resources.ResourceManager> para o seguinte: `ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`  
  
     [!code-csharp[Conceptual.Resources.Locating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/program.cs#1)]
     [!code-vb[Conceptual.Resources.Locating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/module1.vb#1)]  
  
     Se o aplicativo for chamado de Example e você estiver compilando na linha de comando, o comando para o compilador C# será:  
  
    ```console  
    csc Example.cs -res:Greeting.resources  
    ```  
  
     O comando do compilador Visual Basic correspondente é:  
  
    ```console  
    vbc Example.vb -res:Greeting.resources  
    ```  
  
6.  Crie um subdiretório no diretório do aplicativo principal para cada cultura localizada com suporte do aplicativo. Você deve criar um subdiretório ru-RU, um fr-FR e um en-US. O Visual Studio cria esses subdiretórios automaticamente como parte do processo de compilação.  
  
7.  Incorpore os arquivos individuais de culturas específicas .resources a assemblies satélites e os salve no diretório apropriado. O comando para fazer isso para cada arquivo .resources é:  
  
    ```console
    al -target:lib -embed:Greeting.culture.resources -culture:culture -out:culture\Example.resources.dll  
    ```  
  
     onde *cultura* é o nome da cultura cujos recursos o assembly satélite contém. O Visual Studio trata esse processo automaticamente.  
  
 Você pode executar o exemplo. Isso tornará aleatoriamente uma das culturas com suporte a cultura atual e exibirá uma saudação localizada.  
  
<a name="SN"></a>   
## <a name="installing-satellite-assemblies-in-the-global-assembly-cache"></a>Instalação de assemblies satélite no Cache de Assembly Global (GAC)  
 Em vez de instalar assemblies em um subdiretório do aplicativo local, você pode instalá-los no cache de assembly global. Isso é particularmente útil se você tiver bibliotecas de classes e assemblies de recursos de biblioteca de classe usados por vários aplicativos.  
  
 A instalação de assemblies no cache de assembly global exige que eles tenham nomes fortes. Assemblies com nomes fortes são assinados com um par de chaves públicas/privadas válido. Elas contêm informações de versão que o tempo de execução usa para determinar qual assembly usar para atender a uma solicitação de associação. Para obter mais informações sobre nomes fortes e controle de versão, consulte [Controle de versão do assembly](../../../docs/framework/app-domains/assembly-versioning.md). Para obter mais informações sobre nomes fortes, consulte [Assemblies com nome forte](../../../docs/framework/app-domains/strong-named-assemblies.md).  
  
 Quando você estiver desenvolvendo um aplicativo, é improvável que tenha acesso ao par de chaves públicas/privadas final. Para instalar um assembly satélite no cache de assembly global e garantir que ele funcione conforme o esperado, você pode usar uma técnica chamada assinatura atrasada. Quando você atrasar a assinatura de um assembly, no momento da compilação, reserve espaço no arquivo para a assinatura de nome forte. A assinatura real é atrasada até mais tarde, quando o par de chaves públicas/privadas final ficar disponível. Para obter mais informações sobre o processo de assinatura com atraso, consulte [Assinatura com atraso de um assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
### <a name="obtaining-the-public-key"></a>Obtenção da chave pública  
 Para atrasar a assinatura de um assembly, você deve ter acesso à chave pública. Você pode obter a chave pública real da organização para sua empresa que fará a eventual assinatura, ou criar uma chave pública usando a [Ferramenta de Nome Forte (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).  
  
 O comando a seguir Sn.exe cria um par de chaves públicas/privadas de teste. A opção **– k** especifica que Sn.exe deve criar um novo par de chaves e salvá-lo em um arquivo chamado TestKeyPair.snk.  
  
```console
sn –k TestKeyPair.snk   
```  
  
 Você pode extrair a chave pública do arquivo que contém o par de chaves de teste. O comando a seguir extrai a chave pública de TestKeyPair.snk e a salva no PublicKey.snk:  
  
```console
sn –p TestKeyPair.snk PublicKey.snk  
```  
  
### <a name="delay-signing-an-assembly"></a>Atrasando a assinatura de um assembly  
 Depois de obter ou criar a chave pública, use o [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) para compilar o assembly e especificar a assinatura com atraso.  
  
 O comando a seguir Al.exe cria um assembly satélite com nome forte para o aplicativo StringLibrary usando o arquivo strings.ja.resources:  
  
```console 
al -target:lib -embed:strings.ja.resources -culture:ja -out:StringLibrary.resources.dll -delay+ -keyfile:PublicKey.snk  
```  
  
 A opção **-delay+** especifica que o Assembly Linker deve atrasar a assinatura do assembly. A opção **-keyfile** especifica o nome do arquivo da chave que contém a chave pública a ser usada para atrasar a assinatura do assembly.  
  
### <a name="re-signing-an-assembly"></a>Nova assinatura de um assembly com atraso  
 Antes de implantar seu aplicativo, você deve reassinar o assembly satélite com atraso com o par de chaves real. Você pode fazer isso usando Sn.exe.  
  
 O comando a seguir Sn.exe assina StringLibrary.resources.dll com o par de chaves armazenado no arquivo RealKeyPair.snk. A opção **– R** especifica que um assembly assinado anteriormente ou assinado com atraso deve ser assinado novamente.  
  
```console
sn –R StringLibrary.resources.dll RealKeyPair.snk   
```  
  
### <a name="installing-a-satellite-assembly-in-the-global-assembly-cache"></a>Instalação de assemblies satélite no Cache de Assembly Global (GAC)  
 Quando o tempo de execução procura recursos no processo de fallback de recursos, ele examina o [cache de assembly global](../../../docs/framework/app-domains/gac.md) primeiro. (Para obter mais informações, consulte a seção "Processo de fallback de recurso" do tópico [Empacotamento e implantação de recursos](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).) Assim que um assembly satélite é assinado com um nome forte, ele pode ser instalado no cache de assembly global usando a [ferramenta Cache de Assembly Global (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
 O comando a seguir Gacutil.exe instala o StringLibrary.resources.dll no cache de assembly global:  
  
```console
gacutil -i:StringLibrary.resources.dll  
```  
  
 A opção **/i** especifica que Gacutil.exe deve instalar o assembly especificado no cache de assembly global. Após o satélite assembly ser instalado no cache, os recursos que ele contém ficam disponíveis para todos os aplicativos que são projetados para usar o assembly satélite.  
  
### <a name="resources-in-the-global-assembly-cache-an-example"></a>Recursos no Cache de Assembly Global: um exemplo  
 O exemplo a seguir usa um método em uma biblioteca de classes .NET Framework para extrair e retornar uma saudação localizada de um arquivo de recurso. A biblioteca e seus recursos são registrados no cache de assembly global. O exemplo do inclui recursos para as culturas inglesa (Estados Unidos), francesa (França), russa (Rússia) e inglesas. Inglês é a cultura padrão; seus recursos são armazenados no assembly principal. O exemplo inicialmente atrasa a assinatura da biblioteca e seus assemblies satélites com uma chave pública. Em seguida, assina-os novamente com um par de chaves públicas/privadas. Para criar o exemplo, faça o seguinte:  
  
1.  Se você não estiver usando o Visual Studio, use o seguinte comando [Ferramenta de Nome Forte (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) para criar um par de chaves públicas/privadas denominado ResKey.snk:  
  
    ```console
    sn –k ResKey.snk  
    ```  
  
     Se você estiver usando o Visual Studio, use a guia **Assinatura** da caixa de diálogo **Propriedades** do projeto para gerar o arquivo de chave.  
  
2.  Use o seguinte comando [Ferramenta de Nome Forte (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) para criar um arquivo de chave pública denominado PublicKey.snk:  
  
    ```console
    sn –p ResKey.snk PublicKey.snk  
    ```  
  
3.  Crie um arquivo de recurso chamado Strings.resx para conter o recurso para a cultura padrão. Armazene uma única cadeia de caracteres denominada `Greeting` cujo valor é "How do you do?" nesse arquivo.  
  
4.  Para indicar que “en” é a cultura padrão do aplicativo, adicione o seguinte atributo <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> ao arquivo AssemblyInfo do aplicativo ou ao arquivo de código-fonte principal que será compilado no assembly principal do aplicativo:  
  
     [!code-csharp[Conceptual.Resources.Satellites#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#2)]
     [!code-vb[Conceptual.Resources.Satellites#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#2)]  
  
5.  Adicione suporte a culturas adicionais (en-US, fr-FR e ru-RU) ao aplicativo da seguinte maneira:  
  
    -   Para oferecer suporte à cultura inglesa (Estados Unidos) ou “en-US”, crie um arquivo de recurso chamado Strings.en-US.resx ou Strings.en- US.txt e armazene nele uma única cadeia de caracteres denominada `Greeting`, cujo valor é "Hello!".  
  
    -   Para oferecer suporte à cultura francesa (França) ou “fr-FR”, crie um arquivo de recurso chamado Strings.fr-FR.resx ou Strings.fr-FR.txt e armazene nele uma única cadeia de caracteres denominada `Greeting`, cujo valor é "Bon jour!"  
  
    -   Para oferecer suporte à cultura russa (Rússia) ou “ru-RU”, crie um arquivo de recurso chamado Strings.fr-FR.resx ou Strings.ru-RU.txt e armazene nele uma única cadeia de caracteres denominada `Greeting`, cujo valor é "Привет!"  
  
6.  Use [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) para compilar cada texto ou um arquivo de recursos XML em um arquivo binário .resources. A saída é um conjunto de arquivos que têm o mesmo nome de arquivo raiz que os arquivos. resx ou. txt, mas uma extensão .resources. Se você criar o exemplo com o Visual Studio, o processo de compilação será manipulado automaticamente. Se você não estiver usando o Visual Studio, execute o seguinte comando para compilar os arquivos .resx em arquivos .resources:  
  
    ```console
    resgen filename  
    ```  
  
     onde *filename* é o caminho opcional, o nome e a extensão do arquivo. resx ou texto.  
  
7.  Compile o seguinte código-fonte para StringLibrary.vb ou StringLibrary.cs com os recursos da cultura padrão em um assembly de biblioteca assinado com atraso chamado StringLibrary.dll:  
  
    > [!IMPORTANT]
    >  Se você estiver usando a linha de comando em vez do Visual Studio para criar o exemplo, modifique a chamada ao construtor de classe <xref:System.Resources.ResourceManager> para `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`.  
  
     [!code-csharp[Conceptual.Resources.Satellites#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#1)]
     [!code-vb[Conceptual.Resources.Satellites#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#1)]  
  
     O comando para o compilador do C# é:  
  
    ```console
    csc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.cs  
    ```  
  
     O comando do compilador Visual Basic correspondente é:  
  
    ```console  
    vbc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.vb  
    ```  
  
8.  Crie um subdiretório no diretório do aplicativo principal para cada cultura localizada com suporte do aplicativo. Você deve criar um subdiretório ru-RU, um fr-FR e um en-US. O Visual Studio cria esses subdiretórios automaticamente como parte do processo de compilação. Como todos os assemblies satélite têm o mesmo nome de arquivo, os subdiretórios são usados para armazenar assemblies satélite de cultura específica individuais até que eles sejam assinados com um par de chaves públicas/privadas.  
  
9. Incorpore os arquivos individuais de culturas específicas .resources a assemblies satélites assinados com atraso e os salve no diretório apropriado. O comando para fazer isso para cada arquivo .resources é:  
  
    ```console
    al -target:lib -embed:Strings.culture.resources -culture:culture -out:culture\StringLibrary.resources.dll -delay+ -keyfile:publickey.snk  
    ```  
  
     onde *culture* é o nome de uma cultura. Neste exemplo, os nomes de cultura são ru-RU, en-US e fr-FR.  
  
10. Assine novamente a StringLibrary.dll usando a [Ferramenta de Nome Forte (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) da seguinte maneira:  
  
    ```console
    sn –R StringLibrary.dll RealKeyPair.snk  
    ```  
  
11. Assine novamente os assemblies satélite individuais. Para fazer isso, use a [Ferramenta de Nome Forte (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) da seguinte forma para cada assembly satélite:  
  
    ```console
    sn –R StringLibrary.resources.dll RealKeyPair.snk  
    ```  
  
12. Registre a StringLibrary.dll e cada um dos seus assemblies satélites no cache de assembly global usando o comando a seguir:  
  
    ```console
    gacutil -i filename  
    ```  
  
     onde *filename* é o nome do arquivo para registrar.  
  
13. Se você estiver usando o Visual Studio, crie um novo projeto **Aplicativo de Console** chamado `Example`, adicione uma referência à StringLibrary.dll e o seguinte código-fonte a ela e compile.  
  
     [!code-csharp[Conceptual.Resources.Satellites#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/example.cs#3)]
     [!code-vb[Conceptual.Resources.Satellites#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/example.vb#3)]  
  
     Para compilar da linha de comando, use o seguinte comando para o compilador do C#:  
  
    ```console
    csc Example.cs -r:StringLibrary.dll   
    ```  
  
     A linha de comando para o compilador do Visual Basic é:  
  
    ```console
    vbc Example.vb -r:StringLibrary.dll   
    ```  
  
14. Execute Example.exe.  
  
## <a name="see-also"></a>Consulte também  
 [Empacotando e implantando recursos](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
 [Assinar um assembly com atraso](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 [Al.exe (Assembly Linker)](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [Sn.exe (Ferramenta Nome Forte)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [Gacutil.exe (Ferramenta do Cache de Assemblies Global)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 [Recursos em aplicativos de área de trabalho](../../../docs/framework/resources/index.md)
