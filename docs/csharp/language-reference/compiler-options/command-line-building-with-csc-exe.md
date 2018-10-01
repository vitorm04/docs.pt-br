---
title: Build pela linha de comando com csc.exe
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: 4b6dfdbce131371553fc729206de29794266bfbe
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47216351"
---
# <a name="command-line-build-with-cscexe"></a>Build pela linha de comando com csc.exe
Você pode invocar o compilador do C#, digitando o nome do seu arquivo executável (*csc.exe*) em um prompt de comando.

Se você usar a janela do **Prompt de Comando do Desenvolvedor do Visual Studio**, todas as variáveis de ambiente necessárias serão definidas para você. Para obter informações sobre como acessar essa ferramenta, consulte o tópico [Prompt de comando do desenvolvedor para o Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md). 

Se você usa uma janela de Prompt de Comando padrão, deve ajustar seu caminho antes de invocar o *csc.exe* de qualquer subdiretório em seu computador. Você também deve executar o *vsvars32.bat* para definir as variáveis de ambiente adequadas para dar suporte aos builds de linha de comando. Para obter mais informações sobre o *vsvars32.bat*, incluindo instruções sobre como localizá-lo e executá-lo, consulte [Como: configurar variáveis de ambiente para a linha de comando do Visual Studio](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).

Se você estiver trabalhando em um computador que tem apenas o [!INCLUDE[winsdklong](~/includes/winsdklong-md.md)], você poderá usar o compilador do C# no **Prompt de Comando do SDK**, que é aberto na opção de menu **Microsoft .NET Framework SDK**.

Você também pode usar o MSBuild para compilar programas em C# programaticamente. Para mais informações, consulte [MSBuild](/visualstudio/msbuild/msbuild).

O arquivo executável *csc.exe* normalmente está localizado na pasta Microsoft.NET\Framework\\*\<Versão>* no diretório *Windows*. O local pode variar dependendo da configuração exata de um computador específico. Se mais de uma versão do .NET Framework estiver instalada em seu computador, você encontrará várias versões desse arquivo. Para obter mais informações sobre essas instalações, consulte [Determinando qual versão do .NET Framework está instalada](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).

> [!TIP]
>  Quando você compila um projeto usando o IDE do Visual Studio, você pode exibir o comando **csc** e suas opções de compilador associadas na janela **Saída**. Para exibir essas informações, siga as instruções em [Como exibir, salvar e configurar arquivos de log de build](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log), para alterar o nível de detalhes dos dados de log para **Normal** ou **Detalhado**. Depois de recompilar o projeto, pesquise na janela **Saída** por **csc** para localizar a invocação do compilador do C#.

 **Neste tópico**

- [Regras para sintaxe de linha de comando](#-rules-for-command-line-syntax-for-the-c-compiler)

- [Linhas de comando de exemplo](#sample-command-lines-for-the-c-compiler)

- [Diferenças entre as saídas dos compiladores do C# e do C++](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a>Regras para sintaxe de linha de comando para o compilador do C#

O compilador do C# usa as seguintes regras para interpretar os argumentos fornecidos na linha de comando do sistema operacional:

- Os argumentos são delimitados por espaço em branco, que é um espaço ou uma tabulação.

- O caractere de acento circunflexo (^) não é reconhecido como um caractere de escape ou um delimitador. O caractere é tratado pelo analisador de linha de comando no sistema operacional antes de ser passado para a matriz `argv` no programa.

- Uma cadeia de caracteres entre aspas duplas ("cadeia de caracteres") é interpretada como um único argumento, independentemente do espaço em branco que está contido nela. Uma cadeia de caracteres entre aspas pode ser inserida em um argumento.

- Aspas duplas precedidas por uma barra invertida (\\") são interpretados como um caractere literal de aspas duplas (").

- As barras invertidas são interpretadas literalmente, a menos que precedam imediatamente as aspas duplas.

- Se um número par de barras invertidas for seguido por aspas duplas, uma barra invertida será colocada na matriz `argv` para cada par de barras invertidas e aspas duplas serão interpretadas como um delimitador de cadeia de caracteres.

- Se um número ímpar de barras invertidas for seguido por aspas duplas, uma barra invertida será colocada na matriz `argv` para cada par de barras invertidas e aspas duplas serão "escapadas" pela barra invertida restante. Isso fará com que aspas duplas (") literais sejam adicionadas na `argv`.

## <a name="sample-command-lines-for-the-c-compiler"></a>Linhas de comando de exemplo para o compilador do C#

- Compila o *File.cs* produzindo o *File.exe*:

```console
csc File.cs 
```

- Compila o *File.cs* produzindo o *File.dll*:

```console
csc -target:library File.cs
```

- Compila o *File.cs* e cria o *My.exe*:

```console
csc -out:My.exe File.cs
```

- Compila todos os arquivos do C# no diretório atual, com otimizações habilitadas e define o símbolo de DEPURAÇÃO. A saída é *File2.exe*:

```console
csc -define:DEBUG -optimize -out:File2.exe *.cs
```

- Compila todos os arquivos do C# no diretório atual, produzindo uma versão de depuração de *File2.dll*. Logotipos e avisos não são exibidos:

```console
csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
```

- Compila todos os arquivos do C# no diretório atual para *Something.xyz* (uma DLL):

```console
csc -target:library -out:Something.xyz *.cs
```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a>Diferenças entre as saídas dos compiladores do C# e do C++
Não há arquivos de objeto (*.obj*) criados como resultado da invocação do compilador do C#. Os arquivos de saída são criados diretamente. Como um resultado disso, o compilador do C# não precisa de um vinculador.

## <a name="see-also"></a>Consulte também

- [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Opções do compilador de C# listadas em ordem alfabética](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
- [Opções do compilador de C# listadas por categoria](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
- [Main() e argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/index.md)  
- [Argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)  
- [Como exibir argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
- [Como acessar argumentos de linha de comando usando foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
- [Valores de retorno de Main()](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
