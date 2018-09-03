---
title: Empacotando e implantando recursos em aplicativos de área de trabalho
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
- single resource assembly
- satellite assemblies
- default culture for applications
- names [.NET Framework], resources
- fallback process for resources
- grouping cultures
- application resources, deploying
- application resources, naming conventions
- culture, packaging and deploying resources
- resource files, naming conventions
- packaging application resources
- application resources, fallback processes
- resource files, fallback processes
- localizing resources
- neutral cultures
ms.assetid: b224d7c0-35f8-4e82-a705-dd76795e8d16
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7aca04c191234686de5a15cb3dc1336080a3a344
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485697"
---
# <a name="packaging-and-deploying-resources-in-desktop-apps"></a>Empacotando e implantando recursos em aplicativos de área de trabalho
Aplicativos se baseiam no Gerenciador de Recursos do .NET Framework, representado pela classe <xref:System.Resources.ResourceManager>, para recuperar os recursos localizados. O Gerenciador de Recursos pressupõe que um modelo de hub e spoke é usado para empacotar e implantar recursos. O hub é o principal assembly que contém o código executável não localizável e os recursos para uma única cultura, chamada de cultura neutra ou padrão. O padrão é a cultura de fallback para o aplicativo; é a cultura que tem os recursos utilizados quando não há recursos localizados disponíveis. Cada spoke conecta-se a um assembly satélite que contém os recursos para uma única cultura, mas não contém nenhum código.  
  
 Há várias vantagens para este modelo:  
  
-   Você pode adicionar recursos de culturas novas incrementalmente depois de ter implantado um aplicativo. Como o desenvolvimento posterior de recursos específicos da cultura pode exigir uma quantidade significativa de tempo, isso permite que você libere seu aplicativo principal primeiro e forneça recursos específicos de cultura em uma data posterior.  
  
-   Você pode atualizar e alterar assemblies de satélite do aplicativo sem recompilar o aplicativo.  
  
-   Um aplicativo precisa carregar apenas os assemblies de satélite que contêm os recursos necessários para uma determinada cultura. Isso pode reduzir significativamente o uso de recursos do sistema.  
  
 No entanto, também há desvantagens para este modelo:  
  
-   Você deve gerenciar vários conjuntos de recursos.  
  
-   Aumenta o custo inicial de um aplicativo de teste, porque você deve testar várias configurações. Observe que a longo prazo será mais fácil e menos dispendioso para testar um aplicativo básico com vários satélites que testar e manter várias versões internacionais paralelas.  
  
## <a name="resource-naming-conventions"></a>Convenções de Nomenclatura do Recurso  
 Ao empacotar os recursos de seu aplicativo, você deve nomeá-los usando as convenções de nomenclatura esperadas pelo Common Language Runtime. O tempo de execução identifica um recurso pelo seu nome de cultura. Cada cultura tem um nome exclusivo, que normalmente é uma combinação de um nome de cultura de duas letras minúsculas associado a um idioma e, se necessário, um nome de subcultura de duas letras maiúsculas associado a um país ou região. O nome de subcultura vem depois do nome da cultura, separado por um traço (-). Exemplos incluem ja-JP para japonês falado no Japão, en-US para inglês falado nos Estados Unidos, de-DE para alemão falado na Alemanha, ou de-AT para alemão falado na Áustria. Consulte a [Referência de API de suporte ao idioma nacional (NLS)](https://go.microsoft.com/fwlink/?LinkId=200048) na Central de desenvolvedores Go Global para obter uma lista completa de nomes de cultura.  
  
> [!NOTE]
>  Para obter informações sobre como criar arquivos de recursos, consulte [Criando arquivos de recursos](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md) e [Criando assemblies satélite](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md).  
  
<a name="cpconpackagingdeployingresourcesanchor1"></a>   
## <a name="the-resource-fallback-process"></a>O Processo de Fallback do Recurso  
 O modelo de hub e spoke para empacotamento e implantação de recursos usa um processo de fallback para localizar recursos apropriados. Se o usuário de um aplicativo solicitar um recurso localizado que não esteja disponível, o Common Language Runtime pesquisará a hierarquia das culturas em busca de um recurso de fallback apropriado que mais se aproxime da solicitação do aplicativo do usuário e gerará uma exceção apenas como último recurso. Em cada nível da hierarquia, se um recurso apropriado for encontrado, ele será usado pelo tempo de execução. Se o recurso não for encontrado, a pesquisa continuará até o próximo nível.  
  
 Para melhorar o desempenho da pesquisa, aplique o atributo <xref:System.Resources.NeutralResourcesLanguageAttribute> para seu assembly principal e passe o nome da linguagem neutra que funcione com o assembly principal.  
  
> [!TIP]
>  Você poderá usar o elemento de configuração [\<relativeBindForResources >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) para otimizar o processo de fallback de recurso e o processo pelo qual o tempo de execução testa assemblies de recursos. Para obter mais informações, consulte a seção [Otimizar o processo de fallback do recurso](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#Optimizing).  
  
 O processo de fallback de recurso envolve as seguintes etapas:  
  
1.  O tempo de execução primeiro verifica o [cache de assembly global](../../../docs/framework/app-domains/gac.md) para um assembly que coincide com a cultura solicitada para seu aplicativo.  
  
     O cache de assembly global pode armazenar assemblies de recursos que são compartilhados por vários aplicativos. Isso faz com que você não precise incluir conjuntos de recursos específicos na estrutura de diretórios de cada aplicativo que você criar. Se o tempo de execução encontra uma referência ao assembly, ele pesquisa o assembly para o recurso solicitado. Se ele encontrar a entrada no assembly, ele usa o recurso solicitado. Se não encontrar a entrada, ele continua a pesquisa.  
  
2.  Em seguida, o tempo de execução verifica no diretório do assembly em execução se há um diretório que corresponda à cultura solicitada. Se ele encontrar o diretório, ele procurará nesse diretório um assembly satélite válido para a cultura solicitada. O tempo de execução, em seguida, procura o assembly satélite para o recurso solicitado. Se encontrar o recurso no assembly, ele o utiliza. Se não encontrar o recurso, ele continua a pesquisa.  
  
3.  Em seguida, o tempo de execução consulta o Windows Installer para determinar se o assembly satélite deve ser instalado sob demanda. Se sim, ele faz a instalação, carrega o assembly e as pesquisa o assembly satélite ou o recurso solicitado. Se encontrar o recurso no assembly, ele o utiliza. Se não encontrar o recurso, ele continua a pesquisa.  
  
4.  O tempo de execução gera o evento <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> para indicar que não é possível localizar o assembly satélite. Se você optar por tratar do evento, o manipulador de eventos pode retornar uma referência ao assembly satélite cujos recursos serão usados para a pesquisa. Caso contrário, o manipulador de eventos retornará `null` e continuará a pesquisa.  
  
5.  Em seguida, o tempo de execução pesquisa o cache de assembly global novamente, desta vez para o assembly pai da cultura solicitada. Se o assembly pai existe no cache de assembly global, o tempo de execução procura o assembly para o recurso solicitado.  
  
     A cultura pai é definida como a cultura de fallback apropriada. Considere a cultura pai como candidata de fallback, pois fornecer qualquer recurso é preferível para lançar uma exceção. Esse processo também permite a reutilização de recursos. Você deve incluir um recurso específico no nível pai somente se a cultura filho não precisa localizar o recurso solicitado. Por exemplo, se você fornecer assemblies de satélite para en (inglês neutro), en-GB (inglês falado no Reino Unido) e en-US (inglês falado nos Estados Unidos), o satélite en conteria a terminologia comum e os satélites en-GB e en-US poderiam fornecer substitutos somente para os termos que são diferentes.  
  
6.  Em seguida, o tempo de execução verifica no diretório do assembly em execução se este contém um diretório pai. Se houver um diretório pai, o tempo de execução procura no diretório um assembly satélite válido para a cultura pai. Se encontrar o assembly, o tempo de execução pesquisa o assembly para o recurso solicitado. Se encontrar o recurso, ele o utiliza. Se não encontrar o recurso, ele continua a pesquisa.  
  
7.  Em seguida, o tempo de execução consulta o Windows Installer para determinar se o assembly satélite pai deve ser instalado sob demanda. Se sim, ele faz a instalação, carrega o assembly e as pesquisa o assembly satélite ou o recurso solicitado. Se encontrar o recurso no assembly, ele o utiliza. Se não encontrar o recurso, ele continua a pesquisa.  
  
8.  O tempo de execução gera o evento <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> para indicar que não é possível localizar o recurso de fallback apropriado. Se você optar por tratar do evento, o manipulador de eventos pode retornar uma referência ao assembly satélite cujos recursos serão usados para a pesquisa. Caso contrário, o manipulador de eventos retornará `null` e continuará a pesquisa.  
  
9. Em seguida, o tempo de execução pesquisa assemblies pai, como nas três etapas anteriores, por meio de vários níveis possíveis. Cada cultura tem apenas um pai, que é definido pela propriedade <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType>, mas um pai pode ter seu próprio pai. A pesquisa de culturas pai para quando a propriedade <xref:System.Globalization.CultureInfo.Parent%2A> de uma cultura retorna <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Para o fallback do recurso, a cultura invariável não é considerada uma cultura pai ou uma cultura que pode ter recursos.  
  
10. Se a cultura originalmente especificada e todos os pais foram pesquisados e o recurso ainda não foi encontrado, o recurso para a cultura (fallback) padrão será usado. Normalmente, os recursos para a cultura padrão são incluídos no assembly do aplicativo principal. No entanto, você pode especificar um valor de <xref:System.Resources.UltimateResourceFallbackLocation.Satellite> para a propriedade <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> do atributo <xref:System.Resources.NeutralResourcesLanguageAttribute> para indicar que o local de fallback final de recursos é um assembly satélite, em vez de um assembly principal.  
  
    > [!NOTE]
    >  O recurso padrão é o único recurso que pode ser compilado com o assembly principal. A menos que você especifique um assembly satélite usando o atributo <xref:System.Resources.NeutralResourcesLanguageAttribute>, ele é o fallback final (pai final). Portanto, é recomendável que você sempre inclua um conjunto padrão de recursos no seu assembly principal. Isso ajuda a evitar que exceções sejam lançadas. Com a inclusão de um arquivo de recurso padrão você fornece um fallback para todos os recursos e garante que pelo menos um recurso está sempre presente para o usuário, mesmo se este não for específico de nenhuma cultura.  
  
11. Por fim, se o tempo de execução não encontrar um recurso para uma cultura (fallback) padrão, uma exceção <xref:System.Resources.MissingManifestResourceException> ou <xref:System.Resources.MissingSatelliteAssemblyException> será gerada para indicar que o recurso não pôde ser encontrado.  
  
 Por exemplo, suponha que o aplicativo solicite um recurso localizado para espanhol (México) (a cultura es-MX). O tempo de execução primeiro procura o cache de assembly global para o assembly correspondente a es-MX, mas não encontra-o. O tempo de execução, em seguida, procura no diretório do assembly em execução por um diretório de es-MX. Em caso de falha, o tempo de execução procura o cache de assembly global novamente por um assembly pai que reflita a cultura de fallback apropriada — neste caso, es (espanhol). Se o assembly pai não for encontrado, o tempo de execução procura todos os níveis possíveis de assemblies pai para a cultura es-MX até encontrar um recurso correspondente. Se um recurso não for encontrado, o tempo de execução usa o recurso para a cultura padrão.  
  
<a name="Optimizing"></a>   
### <a name="optimizing-the-resource-fallback-process"></a>Otimizando o Processo de Fallback do Recurso  
 Sob as seguintes condições, você pode otimizar o processo pelo qual o tempo de execução procura recursos em assemblies satélites  
  
-   Assemblies satélite são implantados no mesmo local que o assembly de código. Se o assembly de código estiver instalado no [Cache de Assembly Global](../../../docs/framework/app-domains/gac.md), os assemblies satélites também são instalados no cache de assembly global. Se o assembly de código é instalado em um diretório, os assemblies satélite são instalados em pastas específicas de cultura do diretório.  
  
-   Assemblies satélite não são instalados sob demanda.  
  
-   O código do aplicativo não processa o evento <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.  
  
 Otimiza a investigação de assemblies satélite, incluindo o elemento [ \<relativeBindForResources >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) e a configuração do seu atributo `enabled` para `true` no arquivo de configuração do aplicativo, conforme mostrado no exemplo a seguir.  
  
```xml  
<configuration>  
   <runtime>  
      <relativeBindForResources enabled="true" />  
   </runtime>  
</configuration>  
```  
  
 A investigação otimizada por assemblies satélite é um recurso opcional. Ou seja, o tempo de execução segue as etapas documentadas em [O Processo de fallback do recurso](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#cpconpackagingdeployingresourcesanchor1), a menos que o elemento [\<relativeBindForResources >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) esteja presente no arquivo de configuração do aplicativo e seu atributo `enabled` esteja definido como `true`. Neste caso, o processo de investigação de um assembly satélite é modificado conforme a seguir:  
  
-   O tempo de execução usa o local do assembly de código pai para investigar o assembly satélite. Se o assembly pai estiver instalado no cache de assembly global, o tempo de execução investiga o cache, mas não o diretório do aplicativo. Se o assembly pai estiver instalado em um diretório de aplicativo, o tempo de execução investiga o diretório do aplicativo, mas não no cache de assembly global.  
  
-   O tempo de execução não consulta o Windows Installer para instalação sob demanda dos assemblies satélites.  
  
-   Se a investigação de um assembly de recurso específico falhar, o tempo de execução não gerará o evento <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.  
  
### <a name="ultimate-fallback-to-satellite-assembly"></a>Fallback Final para Assembly Satélite  
 Você pode, opcionalmente, remover recursos do assembly principal e especificar que o tempo de execução deve carregar os recursos de fallback finais a partir de um assembly satélite que corresponda a uma cultura específica. Para controlar o processo de fallback, você deve usar o construtor <xref:System.Resources.NeutralResourcesLanguageAttribute.%23ctor%28System.String%2CSystem.Resources.UltimateResourceFallbackLocation%29?displayProperty=nameWithType> e fornecer um valor para o parâmetro <xref:System.Resources.UltimateResourceFallbackLocation> que especifica se o Gerenciador de Recursos deve extrair os recursos de fallback do assembly principal ou de um assembly satélite.  
  
 O exemplo a seguir usa o atributo <xref:System.Resources.NeutralResourcesLanguageAttribute> para armazenar recursos de fallback do aplicativo em um assembly satélite para o idioma francês (fr).  O exemplo possui dois arquivos de recurso com base em texto que definem um recurso de cadeia de caracteres único chamado `Greeting`. O primeiro, resources.fr.txt, contém um recurso de idioma francês.  
  
```  
Greeting=Bon jour!  
```  
  
 O segundo, resources.ru.fr.txt, contém um recurso de idioma russo.  
  
```  
Greeting=Добрый день  
```  
  
 Esses dois arquivos são compilados em arquivos .resources através da execução do [gerador de arquivo de recurso (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) a partir da linha de comando.  Para o recurso de idioma francês, o comando é:  
  
 **resgen.exe resources.fr.txt**  
  
 Para o recurso de idioma russo, o comando é:  
  
 **resgen.exe resources.ru.txt**  
  
 Os arquivos .resources são incorporados em bibliotecas de vínculo dinâmico através da execução do [vinculador de assembly (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) a partir do comando de linha para o recurso de idioma francês da seguinte maneira:  
  
 **al /t:lib /embed:resources.fr.resources /culture:fr /out:fr\Example1.resources.dll**  
  
 e para o recurso de idioma russo da seguinte maneira:  
  
 **al /t:lib /embed:resources.ru.resources /culture:ru /out:ru\Example1.resources.dll**  
  
 O código-fonte do aplicativo reside em um arquivo chamado Example1.cs ou Example1.vb. Ele inclui o atributo <xref:System.Resources.NeutralResourcesLanguageAttribute> para indicar que o recurso de aplicativo padrão está no subdiretório fr. Ele cria uma instância do Gerenciador de Recursos, recupera o valor do recurso `Greeting` e o exibe para o console.  
  
 [!code-csharp[Conceptual.Resources.Packaging#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.packaging/cs/example1.cs#1)]
 [!code-vb[Conceptual.Resources.Packaging#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.packaging/vb/example1.vb#1)]  
  
 Em seguida, você pode compilar o código-fonte C# na linha de comando da seguinte maneira:  
  
```console 
csc Example1.cs
```
  
 A linha de comando para o compilador do Visual Basic é bastante semelhante:  
  
```console
vbc Example1.vb
```  
  
 Como não há recursos incorporados no assembly principal, você não precisa compilar usando o comutador `/resource`.  
  
 Quando você executar o exemplo a partir de um sistema cujo idioma for diferente de russo, ele exibe a seguinte saída:  
  
```  
Bon jour!  
```  
  
## <a name="suggested-packaging-alternative"></a>Alternativa de Empacotamento Sugerida  
 Restrições de tempo ou orçamento podem impedir a criação de um conjunto de recursos para cada subcultura suportada pelo seu aplicativo. Em vez disso, você pode criar um assembly satélite único para uma cultura pai que todos as subculturas relacionadas podem usar. Por exemplo, você pode fornecer um único assembly satélite em inglês (en) que é recuperado por usuários que solicitam recursos em inglês específicos de região e um único assembly satélite alemão (de) para os usuários que solicitam recursos em alemão específica da região. Por exemplo, as solicitações para alemão falado na Alemanha (de-DE), Áustria (de-AT) e da Suíça (de-CH) fariam fallback para o assembly satélite alemão (de). Os recursos padrão são o fallback final e, portanto, devem ser os recursos que serão solicitados pela maioria dos usuários do seu aplicativo, então escolha cuidadosamente esses recursos. Essa abordagem implanta recursos que são menos culturalmente específicos, mas podem reduzir significativamente os custos de localização do seu aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Recursos em aplicativos de área de trabalho](../../../docs/framework/resources/index.md)  
 [Cache de assembly global](../../../docs/framework/app-domains/gac.md)  
 [Criando arquivos de recurso](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)  
 [Criando assemblies satélite](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
