---
title: Compilando pela linha de comando com csc.exe | Microsoft Docs
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
caps.latest.revision: 28
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: aa6dd9801a141ec430bc291302fe74c35057f117
ms.lasthandoff: 03/13/2017

---
# <a name="command-line-building-with-cscexe"></a>Compilando pela linha de comando com csc.exe
Você pode invocar o compilador do C#, digitando o nome do seu arquivo executável (csc.exe) em um prompt de comando.  
  
 Se você usar a janela do **Prompt de Comando Visual Studio**, todas as variáveis de ambiente necessárias serão definidas para você. No Windows 7, você pode acessar essa janela no menu **Iniciar**, abrindo o Microsoft Visual Studio *Versão*\pasta de Ferramentas do Visual Studio. No Windows 8, o Prompt de Comando Visual Studio é chamado de **Prompt de Comando do Desenvolvedor para VS2012** e você pode localizá-lo pesquisando na tela inicial.  
  
 Se você usa uma janela de Prompt de Comando padrão, deve ajustar seu caminho antes de invocar o csc.exe de qualquer subdiretório em seu computador. Você também deve executar o vsvars32.bat para definir as variáveis de ambiente adequadas para dar suporte aos builds de linha de comando. Para obter mais informações sobre o vsvars32.bat, incluindo instruções sobre como localizá-lo e executá-lo, consulte [Como definir variáveis de ambiente para a linha de comando do Visual Studio](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).  
  
 Se você estiver trabalhando em um computador que tem apenas o [!INCLUDE[winsdklong](../../../csharp/language-reference/compiler-options/includes/winsdklong_md.md)], você poderá usar o compilador do C# no **Prompt de Comando do SDK**, que é aberto na opção de menu **Microsoft .NET Framework SDK**.  
  
 Você também pode usar o MSBuild para compilar programas em C# programaticamente. Para mais informações, consulte [MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild1).  
  
 O arquivo executável csc.exe normalmente está localizado na pasta Microsoft.NET\Framework\\*Versão*, no diretório do Windows. O local pode variar dependendo da configuração exata de um computador específico. Se mais de uma versão do .NET Framework estiver instalada em seu computador, você encontrará várias versões desse arquivo. Para obter mais informações sobre essas instalações, consulte [Determinando qual versão do .NET Framework está instalada](http://msdn.microsoft.com/en-us/1a87cc6a-1c4b-4c38-b878-faa9b3beae3c).  
  
> [!TIP]
>  Quando você compila um projeto usando o IDE do Visual Studio, você pode exibir o comando **csc** e suas opções de compilador associadas na janela **Saída**. Para exibir essas informações, siga as instruções em [Como exibir, salvar e configurar arquivos de log de build](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7), para alterar o nível de detalhes dos dados de log para **Normal** ou **Detalhado**. Depois de recompilar o projeto, pesquise na janela **Saída** por **csc** para localizar a invocação do compilador do C#.  
  
 **Neste tópico**  
  
-   [Regras para sintaxe de linha de comando](#vcconcommand-linebuildinganchor1)  
  
-   [Linhas de comando de exemplo](#vcconcommand-linebuildinganchor2)  
  
-   [Diferenças entre as saídas dos compiladores do C# e C++](#vcconcommand-linebuildinganchor3)  
  
##  <a name="vcconcommand-linebuildinganchor1"></a> Regras para sintaxe de linha de comando para o compilador do C#  
 O compilador do C# usa as seguintes regras para interpretar os argumentos fornecidos na linha de comando do sistema operacional:  
  
-   Os argumentos são delimitados por espaço em branco, que é um espaço ou uma tabulação.  
  
-   O caractere de acento circunflexo (^) não é reconhecido como um caractere de escape ou um delimitador. O caractere é tratado pelo analisador de linha de comando no sistema operacional antes de ser passado para a matriz argv no programa.  
  
-   Uma cadeia de caracteres entre aspas duplas ("cadeia de caracteres") é interpretada como um único argumento, independentemente do espaço em branco que está contido nela. Uma cadeia de caracteres entre aspas pode ser inserida em um argumento.  
  
-   Aspas duplas precedidas por uma barra invertida (\\") são interpretados como um caractere literal de aspas duplas (").  
  
-   As barras invertidas são interpretadas literalmente, a menos que precedam imediatamente as aspas duplas.  
  
-   Se um número par de barras invertidas for seguido por aspas duplas, uma barra invertida será colocada na matriz argv para cada par de barras invertidas e aspas duplas serão interpretadas como um delimitador de cadeia de caracteres.  
  
-   Se um número ímpar de barras invertidas for seguido por aspas duplas, uma barra invertida será colocada na matriz argv para cada par de barras invertidas e aspas duplas serão "ignoradas" pela barra invertida restante. Isso fará com que aspas duplas (") literais sejam adicionadas na argv.  
  
##  <a name="vcconcommand-linebuildinganchor2"></a> Linhas de comando de exemplo para o compilador do C#  
  
-   Compila o File.cs produzindo o File.exe:  
  
    ```  
    csc File.cs   
    ```  
  
-   Compila o File.cs produzindo o File.dll:  
  
    ```  
    csc /target:library File.cs  
    ```  
  
-   Compila o File.cs e cria o My.exe:  
  
    ```  
    csc /out:My.exe File.cs  
    ```  
  
-   Compila todos os arquivos do C# no diretório atual, com otimizações e define o símbolo de DEPURAÇÃO. A saída é File2.exe:  
  
    ```  
    csc /define:DEBUG /optimize /out:File2.exe *.cs  
    ```  
  
-   Compila todos os arquivos do C# no diretório atual, produzindo uma versão de depuração de File2.dll. Logotipos e avisos não são exibidos:  
  
    ```  
    csc /target:library /out:File2.dll /warn:0 /nologo /debug *.cs  
    ```  
  
-   Compila todos os arquivos do C# no diretório atual para Something.xyz (uma DLL):  
  
    ```  
    csc /target:library /out:Something.xyz *.cs  
    ```  
  
##  <a name="vcconcommand-linebuildinganchor3"></a> Diferenças entre as saídas dos compiladores do C# e C++  
 Não há arquivos de objeto (.obj) criados como resultado da invocação do compilador do C#. Os arquivos de saída são criados diretamente. Como um resultado disso, o compilador do C# não precisa de um vinculador.  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [Opções do compilador C# listadas em ordem alfabética](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)   
 [Opções do Compilador do C# Listadas por Categoria](../../../csharp/language-reference/compiler-options/listed-by-category.md)   
 [Main() e argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/index.md)   
 [Argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)   
 [Como exibir argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [Como acessar argumentos de linha de comando usando foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)   
 [Valores de retorno de Main()](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
