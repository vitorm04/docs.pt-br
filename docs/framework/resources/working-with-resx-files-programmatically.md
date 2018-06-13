---
title: Trabalhando com arquivos .resx de forma programática
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resource files, .resx files
- .resx files
ms.assetid: 168f941a-2b84-43f8-933f-cf4a8548d824
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 569f2d59bb2abf013a87bdaa694a7fcf36c70042
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398827"
---
# <a name="working-with-resx-files-programmatically"></a>Trabalhando com arquivos .resx de forma programática
Como arquivos de recurso XML (.resx) devem conter XML bem definido, incluindo um cabeçalho que deve seguir um esquema específico seguido por dados em pares nome/valor, você pode concluir que criar esses arquivo manualmente é algo propenso a erros. Como alternativa, você pode criar arquivos .resx com programação usando tipos e membros da biblioteca de classes .NET Framework. Você também pode usar a biblioteca de classes .NET Framework para recuperar os recursos que são armazenados em arquivos .resx. Este tópico explica como você pode usar os tipos e membros no namespace <xref:System.Resources> para trabalhar com arquivos .resx.  
  
 Observe que este artigo discute como trabalhar com arquivos XML (.resx) que contêm recursos. Para obter informações sobre como trabalhar com arquivos de recurso binário que foram inseridos em assemblies, consulte o tópico <xref:System.Resources.ResourceManager>.  
  
> [!WARNING]
>  Também há outras maneiras de trabalhar com arquivos .resx além de programação. Quando você adiciona um arquivo de recurso a um projeto do Visual Studio, o Visual Studio fornece uma interface para criar e manter um arquivo .resx e converte automaticamente o arquivo .resx em um arquivo .resources no tempo de compilação. Você também pode usar um editor de texto para manipular um arquivo .resx diretamente. No entanto, para evitar danificar o arquivo, tenha cuidado para não modificar nenhuma informação binária armazenada nele.  
  
## <a name="creating-a-resx-file"></a>Criando um arquivo .resx  
 Você pode usar a classe <xref:System.Resources.ResXResourceWriter?displayProperty=nameWithType> para criar um arquivo .resx com programação seguindo estas etapas:  
  
1.  Crie uma instância de um objeto <xref:System.Resources.ResXResourceWriter> chamando o método <xref:System.Resources.ResXResourceWriter.%23ctor%28System.String%29?displayProperty=nameWithType> e fornecendo o nome do arquivo .resx. O nome do arquivo deve incluir a extensão .resx. Se você criar uma instância do objeto <xref:System.Resources.ResXResourceWriter> em um bloco `using`, não será necessário chamar explicitamente o método <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> na etapa 3.  
  
2.  Chame o método <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> para cada recurso que você deseja adicionar ao arquivo. Use as sobrecargas desse método para adicionar cadeia de caracteres, objetos e dados binários (matriz de bytes). Se o recurso for um objeto, ele deverá ser serializável.  
  
3.  Chame o método <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> para gerar o arquivo de recurso e liberar todos os recursos. Se o objeto <xref:System.Resources.ResXResourceWriter> foi criado em um bloco `using`, os recursos são gravados para o arquivo .resx e os recursos usados pelo objeto <xref:System.Resources.ResXResourceWriter> são liberados ao final do bloco `using`.  
  
 O arquivo .resx resultante tem o cabeçalho apropriado e uma marca `data` para cada recurso adicionado pelo método <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType>.  
  
> [!WARNING]
>  Não use arquivos de recurso para armazenar senhas, informações confidenciais ou dados privados.  
  
 O exemplo a seguir cria um arquivo .resx chamado CarResources.resx que armazena seis cadeias de caracteres, um ícone e dois objetos definidos pelo aplicativo (dois objetos `Automobile`). Observe que a classe `Automobile`, que é definida e instanciada no exemplo, é marcada com o atributo <xref:System.SerializableAttribute>.  
  
 [!code-csharp[Conceptual.Resources.ResX#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/create1.cs#1)]
 [!code-vb[Conceptual.Resources.ResX#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/create1.vb#1)]  
  
> [!IMPORTANT]
>  Você também pode usar o Visual Studio para criar arquivos .resx. No tempo de compilação, o Visual Studio usa o [Gerador de Arquivo de Recurso (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) para converter o arquivo .resx em um arquivo de recurso binário (.resources), além de inseri-lo em um assembly de aplicativo ou um assembly satélite.  
  
 Não é possível inserir um arquivo .resx em um executável do tempo de execução ou compilá-lo em um assembly satélite. Você deve converter seu arquivo .resx em um arquivo de recurso binário (.resources) usando o [Gerador de Arquivo de Recurso (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md). O arquivo .resources resultante poderá então ser inserido em um assembly de aplicativo ou um assembly satélite. Para obter mais informações, consulte [Criando arquivos de recursos](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).  
  
## <a name="enumerating-resources"></a>Enumerando recursos  
 Em alguns casos, pode ser útil recuperar todos os recursos, em vez de um recurso específico, de um arquivo .resx. Para fazer isso, você pode usar a classe <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType>, que fornece um enumerador para todos os recursos no arquivo .resx. A classe <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> implementa <xref:System.Collections.IDictionaryEnumerator>, que retorna um objeto <xref:System.Collections.DictionaryEntry> que representa um recurso específico para cada iteração do loop. Sua propriedade <xref:System.Collections.DictionaryEntry.Key%2A?displayProperty=nameWithType> retorna a chave do recurso e sua <xref:System.Collections.DictionaryEntry.Value%2A?displayProperty=nameWithType> propriedade retorna o valor do recurso.  
  
 O exemplo a seguir cria um objeto <xref:System.Resources.ResXResourceReader> para o arquivo CarResources.resx criado no exemplo anterior e itera por meio do arquivo de recurso. Ele adiciona os dois objetos `Automobile` que são definidos no arquivo de recurso para um objeto <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> e adiciona cinco das seis cadeias de caracteres a um objeto <xref:System.Collections.SortedList>. Os valores do objeto <xref:System.Collections.SortedList> são convertidos em uma matriz de parâmetro, que é usada para exibir os títulos de coluna para o console. Os valores da propriedade `Automobile` também são exibidos no console.  
  
 [!code-csharp[Conceptual.Resources.ResX#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/enumerate1.cs#2)]
 [!code-vb[Conceptual.Resources.ResX#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/enumerate1.vb#2)]  
  
## <a name="retrieving-a-specific-resource"></a>Recuperando um recurso específico  
 Além de enumerar os itens em um arquivo .resx, você pode recuperar um recurso específico por nome usando a classe <xref:System.Resources.ResXResourceSet?displayProperty=nameWithType>. O método <xref:System.Resources.ResourceSet.GetString%28System.String%29?displayProperty=nameWithType> recupera o valor de um recurso de cadeia de caracteres nomeado. O método <xref:System.Resources.ResourceSet.GetObject%28System.String%29?displayProperty=nameWithType> recupera o valor de um objeto nomeado ou de dados binários. O método retorna um objeto que deve ser convertido (em C# ou no Visual Basic) em um objeto do tipo apropriado.  
  
 O exemplo a seguir recupera o ícone e a cadeia de caracteres de legenda de um formulário pelos nomes dos recursos. Ele também recupera objetos `Automobile` definido pelo aplicativo usados no exemplo anterior e exibe-os em um controle <xref:System.Windows.Forms.DataGridView>.  
  
 [!code-csharp[Conceptual.Resources.ResX#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/retrieve1.cs#3)]
 [!code-vb[Conceptual.Resources.ResX#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/retrieve1.vb#3)]  
  
## <a name="converting-resx-files-to-binary-resources-files"></a>Convertendo arquivos .resx em arquivos .resources binários  
 Converter arquivos .resx em arquivos de recurso binário inserido (.resources) traz vantagens significativas. Embora os arquivos .resx sejam fáceis de ler e manter durante o desenvolvimento do aplicativo, eles raramente são incluídos em aplicativos acabados. Se eles forem distribuídos com um aplicativo, existirão como arquivos separados do executável do aplicativo e as bibliotecas que o acompanham. Por outro lado, arquivos .resources são inseridos no executável do aplicativo ou nos assemblies que os acompanham. Além disso, para aplicativos localizados, contar com arquivos .resx no tempo de execução coloca a responsabilidade de manipular o fallback de recurso nas mãos do desenvolvedor. Por outro lado, se um conjunto de assemblies de satélite que contêm arquivos .resources inseridos tiver sido criado, o Common Language Runtime manipula o processo de fallback de recurso.  
  
 Para converter um arquivo .resx em um arquivo .resources, use o [Gerador de Arquivo de Recurso (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md), que tem a seguinte sintaxe básica:  
  
 **Resgen.exe** *.resxFilename*  
  
 O resultado é um arquivo de recurso binário que tem o mesmo nome de arquivo raiz que o arquivo .resx e uma extensão de arquivo .resources. Esse arquivo poderá ser compilado em um executável ou uma biblioteca no tempo de compilação. Se você estiver usando o compilador do Visual Basic, use a sintaxe a seguir para inserir um arquivo .resources no executável do aplicativo:  
  
 **vbc** *filename* **.vb -resource:** *.resourcesFilename*  
  
 Se você usar C#, a sintaxe será a seguinte:  
  
 **csc** *filename* **.cs -resource:** *.resourcesFilename*  
  
 O arquivo .resources também pode ser incorporado em um assembly satélite usando o [Vinculador de Assembly (AL.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md), que tem a seguinte sintaxe básica:  
  
 **al** *resourcesFilename* **-out:** *assemblyFilename*  
  
## <a name="see-also"></a>Consulte também  
 [Criando arquivos de recurso](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)  
 [Resgen.exe (Gerador de Arquivo de Recurso)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)  
 [Al.exe (Assembly Linker)](../../../docs/framework/tools/al-exe-assembly-linker.md)
