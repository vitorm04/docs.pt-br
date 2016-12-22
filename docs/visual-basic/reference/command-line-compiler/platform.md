---
title: "/platform (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Opção de compilador /platform [Visual Basic]"
  - "Opção de compilador platform [Visual Basic]"
  - "Opção de compilador -platform [Visual Basic]"
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
caps.latest.revision: 34
caps.handback.revision: 34
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /platform (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica qual versão de plataforma do common language runtime \(CLR\) pode executar o arquivo de saída.  
  
## Sintaxe  
  
```  
/platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## Arguments  
  
|||  
|-|-|  
|Termo|Definição|  
|`x86`|Compila o assembly para ser executado pelo CLR compatível com x86, de 32 bits.|  
|`x64`|Compila o assembly para ser executado pelo CLR de 64 bits em um computador que oferece suporte ao conjunto de instruções de AMD64 ou EM64T.|  
|`Itanium`|Compila o assembly para ser executado pelo CLR de 64 bits em um computador com um processador Itanium.|  
|`arm`|Compila o assembly para ser executado em um computador com um processador ARM \(Advanced RISC Machine\).|  
|`anycpu`|Compila o assembly para ser executado em qualquer plataforma.  O aplicativo será executado como um aplicativo de 32 bits em versões de 32 bits do Windows e como um aplicativo de 64 bits em versões de 64 bits do Windows.  Este sinalizador é o valor padrão.|  
|`anycpu32bitpreferred`|Compila o assembly para ser executado em qualquer plataforma.  O aplicativo será executado como um aplicativo de 32 bits em versões de 32 bits e 64 bits do Windows.  Esse sinalizador é válido somente para executáveis \(.EXE\) e requer [!INCLUDE[net_v45](../../../csharp/language-reference/compiler-options/includes/net_v45_md.md)].|  
  
## Comentários  
 Use a opção `/platform` para especificar o tipo de processador direcionada pelo arquivo de saída.  
  
 Em geral, os assemblies do .NET Framework gravados no Visual Basic serão executados da mesma maneira, independentemente da plataforma.  No entanto, existem alguns casos em que se comportam de formas diferentes em plataformas distintas.  Esses casos comuns são:  
  
-   Estruturas que contêm membros que alteram o tamanho de acordo com a plataforma, como qualquer tipo de ponteiro.  
  
-   Aritmética de ponteiro que inclui tamanhos constantes.  
  
-   As declarações COM ou de invocação de plataforma incorreta que usam `Integer` para identificadores em vez de <xref:System.IntPtr>.  
  
-   Convertendo <xref:System.IntPtr> para `Integer`.  
  
-   Usando a invocação de plataforma ou a interoperabilidade COM com os componentes que não existem em todas as plataformas.  
  
 A opção **\/platform** reduzirá alguns problemas se você souber que fez suposições sobre a arquitetura na qual seu código será executado.  Especificamente:  
  
-   Se decidir atingir uma plataforma de 64 bits e o aplicativo for executado em uma máquina de 32 bits, a mensagem de erro vem muito mais cedo e mais direcionada ao problema do que o erro que ocorre sem usar essa comutador.  
  
-   Se você definir o sinalizador `x86` na opção e, em seguida, o aplicativo for executado em uma máquina de 64 bits, o aplicativo será executado no subsistema WOW em vez de ser executado nativamente.  
  
 Em um sistema operacional do Windows de 64 bits:  
  
-   Assemblies compilados com `/platform:x86` serão executados no CLR de 32 bits em execução no WOW64.  
  
-   Executáveis compilados com o `/platform:anycpu` serão executados no CLR de 64 bits.  
  
-   Uma DLL compilada com o `/platform:anycpu` será executada no mesmo CLR que o processo no qual foi carregado.  
  
-   Executáveis compilados com `/platform:anycpu32bitpreferred` serão executados no CLR de 32 bits.  
  
 Para obter mais informações sobre como desenvolver um aplicativo para ser executado em uma versão de 64 bits do Windows, consulte [Aplicativos de 64 bits](../Topic/64-bit%20Applications.md).  
  
### Para definir \/platform no IDE do Visual Studio  
  
1.  No **Gerenciador de Soluções**, escolha o projeto, abra o menu **Projeto** e, em seguida, clique em **Propriedades**.  
  
     Para obter mais informações, consulte [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/pt-br/983f3c18-832f-4666-afec-74b716ff3e0e).  
  
2.  Na guia **Compilar**, marque ou desmarque a caixa de seleção **Preferir 32 bits** ou na lista **CPU de Destino**, escolha um valor.  
  
     Para obter mais informações, consulte [Página de Compilação, Designer de Projeto \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic).  
  
## Exemplo  
 O exemplo a seguir mostra como usar a opção do compilador `/platform`.  
  
```  
vbc /platform:x86 myFile.vb  
```  
  
## Consulte também  
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)