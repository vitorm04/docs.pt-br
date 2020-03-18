---
title: Assemblies de referência
description: Saiba mais sobre montagens de referência, um tipo especial de montagens em .NET que contêm apenas a superfície pública da API da biblioteca
author: MSDN-WhiteKnight
ms.date: 09/12/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 938942caf81c54a8aa9207dbe87559438ffb252e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79141062"
---
# <a name="reference-assemblies"></a>Assemblies de referência

*Os conjuntos de referência* são um tipo especial de montagem que contém apenas a quantidade mínima de metadados necessários para representar a superfície pública da API da biblioteca. Eles incluem declarações para todos os membros que são significativas ao fazer referência a uma assembléia em ferramentas de construção, mas excluem todas as implementações de membros membros e declarações de membros privados que não tenham impacto observável em seu contrato de API. Em contraste, as assembléias regulares são chamadas *de assembléias de implementação.*

Os conjuntos de referência não podem ser carregados para execução, mas podem ser aprovados como entrada de compilador da mesma forma que os conjuntos de implementação. Os conjuntos de referência são geralmente distribuídos com o Kit de Desenvolvimento de Software (SDK) de uma determinada plataforma ou biblioteca.

O uso de um conjunto de referência permite que os desenvolvedores construam programas que visam uma versão específica da biblioteca sem ter o conjunto completo de implementação para essa versão. Suponha que você tenha apenas a versão mais recente de alguma biblioteca em sua máquina, mas você quer construir um programa que visa uma versão anterior dessa biblioteca. Se você compilar diretamente contra a montagem de implementação, você pode usar inadvertidamente membros da API que não estão disponíveis na versão anterior. Você só vai encontrar este erro ao testar o programa na máquina alvo. Se você compilar contra o conjunto de referência para a versão anterior, você receberá imediatamente um erro de tempo de compilação.

Uma montagem de referência também pode representar um contrato, ou seja, um conjunto de APIs que não correspondem à montagem concreta da implementação. Tais conjuntos de referência, chamados *de conjunto de contratos,* podem ser usados para atingir várias plataformas que suportam o mesmo conjunto de APIs. Por exemplo, o .NET Standard fornece o conjunto de *contratos, netstandard.dll,* que representa o conjunto de APIs comuns compartilhadas entre diferentes plataformas .NET. As implementações dessas APIs estão contidas em diferentes assembléias em diferentes plataformas, como *mscorlib.dll* no .NET Framework ou *System.Private.CoreLib.dll* no .NET Core. Uma biblioteca que tem como alvo o .NET Standard pode ser executada em todas as plataformas que suportam o .NET Standard.

## <a name="using-reference-assemblies"></a>Usando conjuntos de referência

Para usar certas APIs do seu projeto, você deve adicionar referências às suas assembléias. Você pode adicionar referências a conjuntos de implementação ou a assembléias de referência. Recomenda-se que você use conjuntos de referência sempre que estiverem disponíveis. Isso garante que você esteja usando apenas os membros da API suportados na versão de destino, destinado a ser usado por designers de API. O uso do conjunto de referência garante que você não esteja dependendo dos detalhes da implementação.

As montagens de referência para as bibliotecas .NET Framework são distribuídas com pacotes de segmentação. Você pode obtê-los baixando um instalador autônomo ou selecionando um componente no instalador do Visual Studio. Para obter mais informações, consulte [Instalar o .NET Framework para desenvolvedores](../../framework/install/guide-for-developers.md). Para .NET Core e .NET Standard, os conjuntos de referência são automaticamente baixados conforme necessário (via NuGet) e referenciados. Para .NET Core 3.0 ou superior, os conjuntos de referência para a estrutura principal estão no pacote [Microsoft.NETCore.App.Ref](https://www.nuget.org/packages/Microsoft.NETCore.App.Ref) (o pacote [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App) é usado em vez de versões antes de 3.0). Para obter mais informações, consulte [Pacotes, metapacotes e frameworks](../../core/packages.md) no Guia de Núcleo .NET.

Quando você adiciona referências aos conjuntos .NET Framework no Visual Studio usando a caixa de **diálogo Adicionar referência,** você seleciona um conjunto da lista e o Visual Studio encontra automaticamente conjuntos de referência que correspondem à versão de framework de destino selecionada em seu projeto. O mesmo se aplica à adição de referências diretamente no projeto MSBuild usando o item do projeto [Referência:](/visualstudio/msbuild/common-msbuild-project-items#reference) você só precisa especificar o nome do conjunto, não o caminho completo do arquivo. Quando você adiciona referências a esses conjuntos `-reference` na linha de comando usando a opção compilador <xref:Microsoft.CodeAnalysis.Compilation.AddReferences%2A?displayProperty=nameWithType> [(em C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md) e no [Visual Basic)](../../visual-basic/reference/command-line-compiler/reference.md)ou usando o método na API Roslyn, você deve especificar manualmente arquivos de montagem de referência para a versão correta da plataforma de destino. Os arquivos de montagem de referência do Framework .NET estão localizados no *%ProgramFiles(x86)%\\do Reference Assemblys\\Microsoft\\Framework\\. Diretório NETFramework.* Para o .NET Core, você pode forçar a operação de publicação a copiar conjuntos de referência para `PreserveCompilationContext` sua `true`plataforma de destino no subdiretório *de publicação/refs* do diretório de saída, definindo a propriedade do projeto para . Então você pode passar esses arquivos de montagem de referência para o compilador. O `DependencyContext` uso do pacote [Microsoft.Extensions.DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/) pode ajudar a localizar seus caminhos.

Por não conterem nenhuma implementação, as assembléias de referência não podem ser carregadas para execução. Tentar fazer isso resulta <xref:System.BadImageFormatException?displayProperty=nameWithType>em um . Se você quiser examinar o conteúdo de um conjunto de referência, você pode carregá-lo no contexto somente de reflexão no .NET Framework (usando o <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> método) ou no <xref:System.Reflection.MetadataLoadContext> núcleo .NET.

## <a name="generating-reference-assemblies"></a>Gerando montagens de referência

Gerar montagens de referência para suas bibliotecas pode ser útil quando os consumidores de sua biblioteca precisam construir seus programas contra muitas versões diferentes da biblioteca. Distribuir conjuntos de implementação para todas essas versões pode ser impraticável devido ao seu grande tamanho. Os conjuntos de referência são menores em tamanho, e distribuí-los como parte do SDK da sua biblioteca reduz o tamanho do download e economiza espaço em disco.

IDEs e ferramentas de construção também podem aproveitar os conjuntos de referência para reduzir os tempos de compilação no caso de grandes soluções que consistem em várias bibliotecas de classe. Normalmente, em cenários de construção incremental, um projeto é reconstruído quando qualquer um de seus arquivos de entrada são alterados, incluindo os conjuntos de que depende. A montagem da implementação muda sempre que o programador altera a implementação de qualquer membro. A montagem de referência só muda quando sua API pública é afetada. Assim, usar o conjunto de referência como um arquivo de entrada em vez da montagem de implementação permite pular a construção do projeto dependente em alguns casos.

Você pode gerar conjuntos de referência:

- Em um projeto MSBuild, usando a propriedade do [ `ProduceReferenceAssembly` projeto.](/visualstudio/msbuild/common-msbuild-project-properties)
- Ao compilar o programa a partir da `-refonly` linha de comando, `-refout` especificando[(C#](../../csharp/language-reference/compiler-options/refonly-compiler-option.md) / Visual[Basic)](../../visual-basic/reference/command-line-compiler/refonly-compiler-option.md) ou[(C#](../../csharp/language-reference/compiler-options/refout-compiler-option.md) / [Visual Basic)](../../visual-basic/reference/command-line-compiler/refout-compiler-option.md)opções de compilador.
- Ao usar a API Roslyn, <xref:Microsoft.CodeAnalysis.Emit.EmitOptions.IncludePrivateMembers?displayProperty=nameWithType> `false` definindo <xref:Microsoft.CodeAnalysis.Emit.EmitOptions.EmitMetadataOnly?displayProperty=nameWithType> para `true` e <xref:Microsoft.CodeAnalysis.Compilation.Emit%2A?displayProperty=nameWithType> para em um objeto passado para o método.

Se você quiser distribuir conjuntos de referência com pacotes NuGet, você deve incluí-los no subdiretório *de ref\\ * o diretório de pacotes em vez de no subdiretório *lib\\ * usado para conjuntos de implementação.

## <a name="reference-assemblies-structure"></a>Estrutura de montagens de referência

Os conjuntos de referência são uma expansão do conceito relacionado, *conjuntos somente de metadados*. Os assemblies somente de metadados têm seus corpos de método substituídos por um único corpo `throw null`, mas incluem todos os membros, exceto tipos anônimos. A razão `throw null` para o uso de corpos (ao contrário de nenhum corpo) é para que **o PEVerify** possa ser executado e passar (validando assim a completitude dos metadados).

Os assemblies de referência removem ainda mais metadados (membros particulares) de assemblies somente de metadados:

- Um assembly de referência tem somente referências para o que ele precisa na superfície de API. Talvez o assembly real tenha outras referências relacionadas a implementações específicas. Por exemplo, o `class C { private void M() { dynamic d = 1; ... } }` conjunto de referência para `dynamic`não faz referência a nenhum tipo necessário para .
- Membros de função privados (métodos, propriedades e eventos) são removidos nos casos em que sua remoção não afeta nitidamente a compilação. Se não houver [atributos InternalsVisibleTo,](xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute) os membros da função interna também serão removidos.

Os metadados em conjuntos de referência continuam a manter as seguintes informações:

- Todos os tipos, incluindo tipos privados e aninhados.
- Todos os atributos, mesmo os internos.
- Todos os métodos virtuais.
- Implementações explícitas de interface.
- Propriedades e eventos explicitamente implementados, porque seus acessórios são virtuais.
- Todos os campos de estruturas.

Os conjuntos de referência incluem um atributo [Assembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) de referência em nível de montagem. Este atributo pode ser especificado na fonte; então o compilador não precisará sintetizá-lo. Por causa desse atributo, os tempos de execução se recusarão a carregar conjuntos de referência para execução (mas eles podem ser carregados no modo somente de reflexão).

Os detalhes exatos da estrutura de montagem de referência dependem da versão do compilador. Versões mais recentes podem optar por excluir mais metadados se fordeterminado como não afetando a superfície da API pública.

> [!NOTE]
> As informações nesta seção são aplicáveis apenas aos conjuntos de referência gerados pelos compiladores roslyn a partir da versão C# 7.1 ou Visual Basic versão 15.3. A estrutura de montagens de referência para bibliotecas .NET Framework e .NET Core pode diferir em alguns detalhes, pois eles usam seu próprio mecanismo de geração de montagens de referência. Por exemplo, eles podem ter corpos `throw null` de método totalmente vazios em vez do corpo. Mas o princípio geral ainda se aplica: eles não têm implementações de métodos utilizáveis e contêm metadados apenas para membros que têm um impacto observável a partir de uma perspectiva pública de API.

## <a name="see-also"></a>Confira também

- [Assemblies no .NET](index.md)
- [Visão geral do direcionamento de estrutura](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [Como: Adicionar ou remover referências usando o Gerenciador de Referência](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)
