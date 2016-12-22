---
title: "Instru&#231;&#245;es passo a passo: chamando APIs do Windows (Visual Basic) | Microsoft Docs"
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
  - "Chamadas à API, explicações passo a passo [Visual Basic]"
  - "instrução Declare, declarando funções DLL"
  - "Atributo DllImport, chamando API do Windows"
  - "DLLs, Chamando "
  - "invocação de plataforma, explicações passo a passo"
  - "explicações passo a passo [Visual Basic], Chamadas à API"
  - "API do Windows, Chamando "
  - "API do Windows, explicações passo a passo"
ms.assetid: 9280ca96-7a93-47a3-8d01-6d01be0657cb
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: chamando APIs do Windows (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

APIs do Windows são bibliotecas de vínculo dinâmico \(DLLs\) que fazem parte do sistema operacional Windows.  Você as usa para executar tarefas quando é difícil escrever procedimentos equivalentes de sua preferência.  Por exemplo, o Windows fornece uma função chamada `FlashWindowEx` que permite que você crie a barra de título para um aplicativo alternativo entre tonalidades claras e escuras.  
  
 A vantagem de usar APIs do Windows no seu código é que elas podem economizar tempo de desenvolvimento, pois contêm dezenas de funções úteis que já estão escritas, aguardando para serem usadas.  A desvantagem é que APIs do Windows podem ser difíceis de se trabalhar e dificeis de se corrigir quando as coisas dão errado  
  
 APIs do Windows representam uma categoria especial de interoperabilidade.  APIs do Windows não usam código gerenciado, não têm bibliotecas de tipo internas e usam tipos de dados que são diferentes daqueles usados com Visual Studio.  Devido a essas diferenças, e como APIs do Windows não são objetos COM, interoperabilidade com APIs do Windows e o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] é realizada usando invocação de plataforma, ou PInvoke.  Invocação de plataforma é um serviço que ativa o código gerenciado para chamar funções não gerenciadas implementadas em DLLs.  Para obter mais informações, consulte [Consumindo funções de DLL não gerenciadas](../Topic/Consuming%20Unmanaged%20DLL%20Functions.md).  Você pode usar PInvoke em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] usando a instrução `Declare` ou aplicando o atributo `DllImport` a um procedimento vazio.  
  
 Chamadas de API do Windows foram uma parte importante da programação [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] no passado, mas raramente são necessárias com [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)].  Sempre que possível, você deve usar código gerenciado de [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] para executar tarefas, em vez de chamadas API do Windows.  Essa explicação passo a passo fornece informações sobre as situações nas quais o uso de APIs do Windows é necessária.  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## Chamadas de API Usando Declare  
 A maneira mais comum de chamar APIs do Windows é usar a instrução `Declare`.  
  
#### Para declarar um procedimento de DLL  
  
1.  Determine o nome da função que você deseja chamar, mais seus argumentos, tipos de argumento e valor de retorno, bem como o nome e local da DLL que contém.  
  
    > [!NOTE]
    >  Para obter informações completas sobre as APIs do Windows, consulte a documentação do Win32 SDK na Platform SDK Windows API.  Para obter mais informações sobre as constantes que as APIs do Windows usam, examine os arquivos de cabeçalho, como Windows.h incluído no SDK da plataforma.  
  
2.  Abra um novo projeto aplicativo do Windows, clicando em **New** no menu **File** e em seguida, clicando em  **Project** .  A caixa de diálogo **New Project** será exibida.  
  
3.  Selecione  **Aplicativos do Windows**  a partir da lista de modelos de projeto de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  O novo projeto é exibido.  
  
4.  Adicione a seguinte função `Declare` tanto para a classe quanto módulo no qual você deseja usar a DLL:  
  
     [!CODE [VbVbalrInterop#9](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrInterop#9)]  
  
### Partes de Instrução Declare  
 A instrução `Declare` inclui os elementos a seguir.  
  
#### Modificador automático  
 O modificador `Auto` instrui o runtime para converter a sequência de caracteres com base no nome do método de acordo com a regras de tempo de execução de linguagem comum \(ou alias se especificado\).  
  
#### Palavras\-chave Lib e Alias  
 O nome após a palavra\-chave `Function` é o nome que seu programa usa para acessar a função importada.  Ele pode ser o mesmo que o nome real da função que você está chamando, ou você pode usar qualquer nome válido de procedimento e, em seguida, empregar a palavra\-chave `Alias` para especificar o nome real da função que você está chamando.  
  
 Especifique a palavra\-chave `Lib`, seguida do nome e localização do DLL que contém a função que você está chamando.  Você não precisa especificar o caminho para arquivos localizados nas pastas de sistema do Windows.  
  
 Use o `Alias` palavra\-chave se o nome da função chamada não é válido [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] nome do procedimento ou conflita com o nome de outros itens em seu aplicativo.  `Alias`indica o verdadeiro nome da função que está sendo chamado.  
  
#### Declarações de Tipo de Dados e Argumentos  
 Declare os argumentos e seus tipos de dados.  Esta parte pode ser desafiador porque os tipos de dados que o Windows usa não correspondem aos tipos de dados Visual Studio.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]faz uma grande parte do trabalho para você, convertendo os argumentos para tipos de dados compatíveis, um processo chamado  *de empacotamento*.  Você pode controlar explicitamente como argumentos são empacotados usando o atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> definido no namespace <xref:System.Runtime.InteropServices>.  
  
> [!NOTE]
>  Versões anteriores do [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] permitia que você declarar parâmetros `As Any`, que significa que os dados de qualquer dado tipo pode ser usado.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]exige que você use um tipo de dados específico para todas as `Declare` instruções.  
  
#### Constantes API do Windows  
 Alguns argumentos são combinações de constantes.  Por exemplo, a API `MessageBox` mostrada nessa explicação passo a passo aceita um argumento Integer chamado `Typ` que controle como a caixa de mensagem é exibida.  Você pode determinar o valor numérico das constantes examinando o `#define` instruções no arquivo WinUser. H.  Os valores numéricos geralmente são mostrados em hexadecimal, você poderá usar uma calculadora para adicioná\-los e converter em decimal.  Por exemplo, se você desejar combinar as constantes para o estilo de exclamação `MB_ICONEXCLAMATION` 0x00000030 e o estilo de SIm\/Não `MB_YESNO` 0x00000004, você pode adicionar os números e obter um resultado de 0x00000034, ou 52 decimal.  Embora você possa usar diretamente o resultado decimal, é melhor declarar esses valores como constantes em seu aplicativo e combiná\-los usando o operador `Or`.  
  
###### Para declarar constantes para chamadas API do Windows  
  
1.  Consulte a documentação para a função do Windows que você está chamando.  Determine o nome das constantes que são usadas e o nome do arquivo .h que contém os valores numéricos para constantes.  
  
2.  Usar um editor de texto, como o Bloco de Notas, para exibir o conteúdo do arquivo de cabeçalho \(.h\) e localizar os valores associados às constantes que você está usando.  Por exemplo, a API `MessageBox` usa a constante `MB_ICONQUESTION` para mostrar um ponto de interrogação na caixa de mensagem.  A definição de `MB_ICONQUESTION` está na WinUser.h e aparece da seguinte maneira:  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3.  Adicione instruções `Const` equivalentes à sua classe ou módulo para tornar essas constantes disponíveis para seu aplicativo.  Por exemplo:  
  
     [!CODE [VbVbalrInterop#11](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrInterop#11)]  
  
###### Para chamar o procedimento de DLL  
  
1.  Adicionar um botão chamado `Button1` para o formulário de inicialização para seu projeto e em seguida, clique duas vezes nele para exibir seu código.  O manipulador de eventos para o botão é exibido.  
  
2.  Adicione código para o manipulador de eventos `Click` para o botão que é adicionado, para chamar o procedimento e forneça os argumentos apropriados:  
  
     [!CODE [VbVbalrInterop#12](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrInterop#12)]  
  
3.  Execute o projeto pressionando F5.  A caixa de mensagem é exibida com ambos os botões de resposta **Yes** e **No**.  Clique em qualquer um.  
  
#### Empacotamento de Dados  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automaticamente converte os tipos de dados de parâmetros e valores de retorno para chamadas API do Windows, mas você pode usar o atributo `MarshalAs` para especificar tipos de dados não gerenciados que esperam uma API explicitamente.  Para obter mais informações sobre o empacotamento de interoperabilidade, consulte [Realizando marshaling de interoperabilidade](../Topic/Interop%20Marshaling.md).  
  
###### Para usar Declare e MarshalAs em uma chamada de API  
  
1.  Determine o nome da função que você deseja chamar, mais seus argumentos, tipos de dados e valor de retorno.  
  
2.  Para simplificar o acesso ao atributo `MarshalAs`,adicione uma instrução `Imports` à parte superior do código para a classe ou módulo, como no exemplo a seguir:  
  
     [!CODE [VbVbalrInterop#13](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrInterop#13)]  
  
3.  Adicione um protótipo de função para a função importada para a classe ou módulo que estiver usando, e aplique o atributo `MarshalAs` aos parâmetros ou valor de retorno.  No exemplo a seguir, uma chamada de API que espera que o tipo `void*` é empacotada como `AsAny`:  
  
     [!CODE [VbVbalrInterop#14](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrInterop#14)]  
  
## Chamadas API usando DllImport  
 O `DllImport` atributo fornece uma segunda maneira de chamar funções em DLLs sem bibliotecas de tipos.  `DllImport`é basicamente equivalente ao uso de um `Declare` instrução mas oferece mais controle sobre como as funções são chamadas.  
  
 Você pode usar `DllImport` com a maioria das chamadas API do Windows desde que a chamada se refira a um método compartilhado \(às vezes chamado de  *estático* \).  Não é possível usar os métodos que requerem uma instância de uma classe.  Ao contrário das instruções `Declare`, chamadas `DllImport` não podem usar o atributo `MarshalAs`.  
  
#### Para chamar uma API do Windows usando o atributo DllImport  
  
1.  Abra um novo projeto aplicativo do Windows, clicando em **New** no menu **File** e em seguida, clicando em  **Project** .  A caixa de diálogo **New Project** será exibida.  
  
2.  Selecione  **Aplicativos do Windows**  a partir da lista de modelos de projeto de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  O novo projeto é exibido.  
  
3.  Adicione um botão denominado `Button2` para o formulário de inicialização.  
  
4.  Clique duas vezes em `Button2` para abrir o modo de exibição de código para o formulário.  
  
5.  Para simplificar o acesso à `DllImport`,adicione uma instrução `Imports` à parte superior do código para a classe do formulário de inicialização:  
  
     [!CODE [VbVbalrInterop#13](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrInterop#13)]  
  
6.  Declarar uma função vazia que precede a instrução `End Class` para o formulário e nomeie a função `MoveFile`.  
  
7.  Aplicar os modificadores `Public` e `Shared` à função de declaração e definir parâmetros para `MoveFile` baseiados nos argumentos que função API do Windows usa:  
  
     [!CODE [VbVbalrInterop#16](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrInterop#16)]  
  
     Sua função pode ter qualquer nome válido de procedimento; o atributo `DllImport` especifica o nome na DLL.  Ele também trata interoperabilidade de empacotamento para os parâmetros e valores de retorno, para que você possa escolher os tipos de dados do Visual Studio que são semelhantes aos tipos de dados que a API usa..  
  
8.  Aplique o atributo `DllImport` à função vazia.  O primeiro parâmetro é o nome e o local da DLL que contém a função que você está chamando.  Você não precisa especificar o caminho para arquivos localizados nas pastas de sistema do Windows.  O segundo parâmetro é um argumento nomeado que especifica o nome da função na API do Windows.  Neste exemplo, o `DllImport` atributo força chamadas para `MoveFile` sejam encaminhados para `MoveFileW` em KERNEL32.DLL.  O método `MoveFileW` copia um arquivo do caminho `src` para o caminho `dst`.  
  
     [!CODE [VbVbalrInterop#17](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrInterop#17)]  
  
9. Adicione código para o manipulador de eventos `Button2_Click` chamar a função:  
  
     [!CODE [VbVbalrInterop#18](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrInterop#18)]  
  
10. Criar um arquivo chamado Test.txt e coloque\-o na pasta C:\\Tmp em seu disco rígido.  Crie a pasta TMP, se necessário.  
  
11. Pressione F5 para iniciar o aplicativo.  O formulário principal aparece.  
  
12. Clique em **Button2**.  A mensagem "O arquivo foi movido com êxito" será exibida se o arquivo pode ser movido.  
  
## Consulte também  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Auto](../../../visual-basic/language-reference/modifiers/auto.md)   
 [Alias](../../../visual-basic/language-reference/statements/alias-clause.md)   
 [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Criando protótipos em código gerenciado](../Topic/Creating%20Prototypes%20in%20Managed%20Code.md)   
 [Realizando marshaling de um delegado como um método de retorno de chamada](../Topic/Marshaling%20a%20Delegate%20as%20a%20Callback%20Method.md)