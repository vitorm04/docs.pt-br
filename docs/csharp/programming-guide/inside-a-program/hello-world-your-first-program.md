---
title: "Hello World -- seu primeiro programa (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "cs.program"
  - "vs.csharp.startpage.firstapplication"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "exemplos [C#], Hello World"
  - "exemplo Hello World [C#]"
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
caps.latest.revision: 39
caps.handback.revision: 39
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Hello World -- seu primeiro programa (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O procedimento a seguir cria uma versão C\# do tradicional programa "Hello World\!".  O programa exibe a cadeia de caracteres `Hello World!`  
  
 Para obter mais exemplos de conceitos introdutórios, consulte [Introdução ao Visual C\# e ao Visual Basic](/visual-studio/ide/getting-started-with-visual-csharp-and-visual-basic).  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### Para criar e executar um aplicativo de console  
  
1.  Inicie o Visual Studio.  
  
2.  Na barra de menu, escolha **Arquivo**, **Novo**, **Projeto**.  
  
     A Caixa de diálogo **Novo Projeto** é exibida.  
  
3.  Expanda **Instalado**, expanda **Modelos**, expanda **Visual C\#** e escolha **Aplicativo do console**.  
  
4.  Na caixa **Nome**, especifique um nome para o projeto e escolha o botão **OK**.  
  
     O novo projeto aparece no **Gerenciador de Soluções**.  
  
5.  Se Program.cs não estiver aberto no **Editor de Códigos**, abra o menu de atalho para **Program.cs** em **Gerenciador de Soluções** e escolha **Exibir Código**.  
  
6.  Substitua o conteúdo de Program.cs pelo código a seguir.  
  
     [!code-cs[csProgGuide#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_1.cs)]  
  
7.  Escolha a tecla F5 para executar o projeto.  É exibida uma janela do Prompt de Comando que contém a linha `Hello World!`  
  
 Em seguida, as partes importantes desse programa são examinadas.  
  
## Comentários  
 A primeira linha contém um comentário.  Os caracteres `//` convertem o restante da linha em um comentário.  
  
 [!code-cs[csProgGuide#32](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_2.cs)]  
  
 Você também pode inserir comentários colocando\-os entre os caracteres `/*` e `*/`.  Isso é mostrado no exemplo a seguir.  
  
 [!code-cs[csProgGuide#33](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_3.cs)]  
  
## Método Principal  
 Um aplicativo de console C\# deve conter um método `Main`, em que o controle é iniciado e encerrado.  O método `Main` é onde você cria objetos e executa outros métodos.  
  
 O método `Main` é um método [static](../../../csharp/language-reference/keywords/static.md) que reside em uma classe ou estrutura.  No exemplo anterior, “Olá, mundo\!”, ele está em uma classe denominada `Hello`.  Você pode declarar o método `Main` de uma das seguintes maneiras:  
  
-   Pode retornar `void`.  
  
     [!code-cs[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_4.cs)]  
  
-   Também pode retornar um inteiro.  
  
     [!code-cs[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_5.cs)]  
  
-   Com qualquer um dos tipos de retorno, ele pode receber argumentos.  
  
     [!code-cs[csProgGuideMain#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_6.cs)]  
  
     \- ou \-  
  
     [!code-cs[csProgGuideMain#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_7.cs)]  
  
 O parâmetro do método `Main`, `args`, é uma matriz de `string` que contém os argumentos de linha de comando usados para invocar o programa.  Ao contrário do C\+\+, a matriz não inclui o nome do arquivo executável \(exe\).  
  
 Para obter mais informações sobre como usar argumentos de linha de comando, consulte os exemplos em [Main\(\) e argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md) e [Como criar e usar assemblies usando a linha de comando](../Topic/How%20to:%20Create%20and%20Use%20Assemblies%20Using%20the%20Command%20Line%20\(C%23%20and%20Visual%20Basic\).md).  
  
 A chamada a <xref:System.Console.ReadKey%2A> no final do método `Main` impede que a janela do console feche antes que você tenha uma chance de ler a saída ao executar seu programa em modo de depuração, pressionando F5.  
  
## Entrada e Saída  
 Os programas C\# geralmente usam os serviços de entrada\/saída fornecidos pela biblioteca em tempo de execução do .NET Framework.  A instrução `System.Console.WriteLine("Hello World!");` usa o método <xref:System.Console.WriteLine%2A>.  Esse é um dos métodos de saída da classe <xref:System.Console> na biblioteca em tempo de execução.  Exibe o parâmetro de cadeia de caracteres no fluxo de saída padrão seguido por uma nova linha.  Outros métodos <xref:System.Console> estão disponíveis para operações de entrada e saída diferentes.  Se você incluir a diretiva `using System;` no início do programa, você poderá usar diretamente as classes e os métodos <xref:System> sem qualificá\-los totalmente.  Por exemplo, você pode chamar `Console.WriteLine` em vez de `System.Console.WriteLine`:  
  
 [!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_8.cs)]  
  
 [!code-cs[csProgGuide#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_9.cs)]  
  
 Para obter mais informações sobre métodos de entrada\/saída, consulte <xref:System.IO>.  
  
## Compilação e Execução da Linha de Comando  
 Você pode compilar o programa "Hello World\!" usando o comando, em vez do IDE \(Ambiente de Desenvolvimento Integrado\) do Visual Studio.  
  
#### Para compilar e executar a partir de um prompt de comando  
  
1.  Cole o código do procedimento anterior em qualquer editor de texto e salve o arquivo como um arquivo de texto.  Nomeie o arquivo `Hello.cs`.  Arquivos de código\-fonte C\# usam a extensão `.cs`.  
  
2.  Execute uma das etapas a seguir para abrir uma janela de prompt de comando:  
  
    -   No Windows 8, na tela **Iniciar**, pesquise `Prompt de Comando do Desenvolvedor` e então toque ou escolha **Prompt de Comando do Desenvolvedor para VS2012**.  
  
         Uma janela Prompt de Comando do Desenvolvedor é exibida.  
  
    -   No Windows 7, abra o menu **Iniciar**, expanda a pasta para a versão atual do Visual Studio, abra o menu de atalho para **Visual Studio Tools** e então escolha **Prompt de Comando do Desenvolvedor para VS2012**.  
  
         Uma janela Prompt de Comando do Desenvolvedor é exibida.  
  
    -   Habilitar compilações de linha de comando de uma janela de prompt de comando padrão.  
  
         Consulte [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).  
  
3.  Na janela do prompt de comando, navegue até a pasta que contém seu arquivo `Hello.cs`.  
  
4.  Insira o seguinte comando para compilar `Hello.cs`.  
  
     `csc Hello.cs`  
  
     Se o seu programa não tem nenhum erro de compilação, um arquivo executável chamado `Hello.exe` será criado.  
  
5.  Na janela do prompt de comando, insira o seguinte comando para executar o programa:  
  
     `Hello`  
  
 Para obter mais informações sobre o compilador C\# e suas opções, consulte [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md).  
  
## Capítulo do Livro em Destaque  
 [Escrevendo um programa em C\#](http://go.microsoft.com/fwlink/?LinkId=221227) em [Introdução ao Visual C\# 2010](http://go.microsoft.com/fwlink/?LinkId=221214)  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Por dentro de um programa em C\#](../../../csharp/programming-guide/inside-a-program/index.md)   
 [Cadeias de caracteres](../../../csharp/programming-guide/strings/index.md)   
 [Aplicativos C\# de exemplo](http://msdn.microsoft.com/pt-br/9a9d7aaa-51d3-4224-b564-95409b0f3e15)   
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Main\(\) e argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md)   
 [Introdução ao Visual C\# e ao Visual Basic](/visual-studio/ide/getting-started-with-visual-csharp-and-visual-basic)