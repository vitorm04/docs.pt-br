---
title: 'Instruções passo a passo: chamando APIs do Windows'
ms.date: 07/20/2015
helpviewer_keywords:
- DLLs, calling
- Windows API, walkthroughs
- platform invoke, walkthroughs
- API calls [Visual Basic], walkthroughs [Visual Basic]
- Windows API, calling
- walkthroughs [Visual Basic], API calls
- DllImport attribute, calling Windows API
- Declare statement [Visual Basic], declaring DLL functions
ms.assetid: 9280ca96-7a93-47a3-8d01-6d01be0657cb
ms.openlocfilehash: ec6b8ddc8769fadde52aaebd6ad3701183fac77a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74338672"
---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a>Instruções passo a passo: chamando APIs do Windows (Visual Basic)
As APIs do Windows são DLLs (bibliotecas de vínculo dinâmico) que fazem parte do sistema operacional Windows. Você os usa para executar tarefas quando é difícil escrever procedimentos equivalentes de sua preferência. Por exemplo, o Windows fornece uma função chamada `FlashWindowEx` que permite que você crie a barra de título para um aplicativo alternativo entre tonalidades leves e escuras.  
  
 A vantagem de usar APIs do Windows em seu código é que elas podem economizar tempo de desenvolvimento porque contêm dezenas de funções úteis que já foram gravadas e aguardando para serem usadas. A desvantagem é que as APIs do Windows podem ser difíceis de trabalhar e Unforgiving quando as coisas dão errado.  
  
 As APIs do Windows representam uma categoria especial de interoperabilidade. As APIs do Windows não usam código gerenciado, não têm bibliotecas de tipos internas e usam tipos de dados diferentes daqueles usados com o Visual Studio. Devido a essas diferenças, e como as APIs do Windows não são objetos COM, a interoperabilidade com APIs do Windows e a .NET Framework é executada usando a invocação de plataforma, ou PInvoke. A invocação de plataforma é um serviço que permite que o código gerenciado chame funções não gerenciadas implementadas em DLLs. Para obter mais informações, consulte [consumindo funções de dll não gerenciadas](../../../framework/interop/consuming-unmanaged-dll-functions.md). Você pode usar o PInvoke em Visual Basic usando a instrução `Declare` ou aplicando o atributo `DllImport` a um procedimento vazio.  
  
 As chamadas à API do Windows eram uma parte importante da programação de Visual Basic no passado, mas raramente são necessárias com o Visual Basic .NET. Sempre que possível, você deve usar código gerenciado do .NET Framework para executar tarefas, em vez de chamadas à API do Windows. Este passo a passos fornece informações para as situações em que é necessário usar APIs do Windows.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a>Chamadas de API usando declare  
 A maneira mais comum de chamar APIs do Windows é usando a instrução `Declare`.  
  
### <a name="to-declare-a-dll-procedure"></a>Para declarar um procedimento de DLL  
  
1. Determine o nome da função que você deseja chamar, além de seus argumentos, tipos de argumento e valor de retorno, bem como o nome e o local da DLL que o contém.  
  
    > [!NOTE]
    > Para obter informações completas sobre as APIs do Windows, consulte a documentação do SDK do Win32 na API do Windows do SDK da plataforma. Para obter mais informações sobre as constantes que as APIs do Windows usam, examine os arquivos de cabeçalho como o Windows. h incluído com o Platform SDK.  
  
2. Abra um novo projeto de aplicativo do Windows clicando em **novo** no menu **arquivo** e, em seguida, clicando em **projeto**. A caixa de diálogo **Novo Projeto** é exibida.  
  
3. Selecione **aplicativo do Windows** na lista de modelos de projeto Visual Basic. O novo projeto é exibido.  
  
4. Adicione a função `Declare` a seguir à classe ou ao módulo no qual você deseja usar a DLL:  
  
     [!code-vb[VbVbalrInterop#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#9)]  
  
### <a name="parts-of-the-declare-statement"></a>Partes da instrução Declare  
 A instrução `Declare` inclui os elementos a seguir.  
  
#### <a name="auto-modifier"></a>Modificador automático  
 O modificador `Auto` instrui o tempo de execução para converter a cadeia de caracteres com base no nome do método de acordo com Common Language Runtime regras (ou nome do alias, se especificado).  
  
#### <a name="lib-and-alias-keywords"></a>Palavras-chave lib e alias  
 O nome após a palavra-chave `Function` é o nome que seu programa usa para acessar a função importada. Pode ser igual ao nome real da função que você está chamando, ou você pode usar qualquer nome de procedimento válido e, em seguida, empregar a palavra-chave `Alias` para especificar o nome real da função que você está chamando.  
  
 Especifique a palavra-chave `Lib`, seguida pelo nome e o local da DLL que contém a função que você está chamando. Você não precisa especificar o caminho para os arquivos localizados nos diretórios de sistema do Windows.  
  
 Use a palavra-chave `Alias` se o nome da função que você está chamando não for um nome de procedimento de Visual Basic válido ou estiver em conflito com o nome de outros itens em seu aplicativo. `Alias` indica o nome verdadeiro da função que está sendo chamada.  
  
#### <a name="argument-and-data-type-declarations"></a>Declarações de tipo de dados e de argumento  
 Declare os argumentos e seus tipos de dados. Essa parte pode ser desafiadora porque os tipos de dados que o Windows usa não correspondem aos tipos de dados do Visual Studio. Visual Basic faz grande parte do trabalho para você convertendo argumentos para tipos de dados compatíveis, um processo chamado *marshaling*. Você pode controlar explicitamente como os argumentos são empacotados usando o atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> definido no namespace <xref:System.Runtime.InteropServices>.  
  
> [!NOTE]
> As versões anteriores do Visual Basic permitiam que você declarasse parâmetros `As Any`, o que significa que os dados de qualquer tipo de dados poderiam ser usados. Visual Basic requer que você use um tipo de dados específico para todas as instruções `Declare`.  
  
#### <a name="windows-api-constants"></a>Constantes da API do Windows  
 Alguns argumentos são combinações de constantes. Por exemplo, a API de `MessageBox` mostrada neste passo a passos aceita um argumento inteiro chamado `Typ` que controla como a caixa de mensagem é exibida. Você pode determinar o valor numérico dessas constantes examinando as instruções de `#define` no arquivo WinUser. h. Os valores numéricos geralmente são mostrados em hexadecimal, portanto, talvez você queira usar uma calculadora para adicioná-los e convertê-los em decimal. Por exemplo, se você quiser combinar as constantes para o estilo de exclamação `MB_ICONEXCLAMATION` 0x00000030 e o estilo Sim/não `MB_YESNO` 0x00000004, você poderá adicionar os números e obter um resultado de 0x00000034, ou 52 decimal. Embora você possa usar o resultado decimal diretamente, é melhor declarar esses valores como constantes em seu aplicativo e combiná-los usando o operador de `Or`.  
  
##### <a name="to-declare-constants-for-windows-api-calls"></a>Para declarar constantes para chamadas à API do Windows  
  
1. Consulte a documentação da função do Windows que você está chamando. Determine o nome das constantes que ele usa e o nome do arquivo. h que contém os valores numéricos para essas constantes.  
  
2. Use um editor de texto, como o bloco de notas, para exibir o conteúdo do arquivo de cabeçalho (. h) e localize os valores associados às constantes que você está usando. Por exemplo, a API de `MessageBox` usa a constante `MB_ICONQUESTION` para mostrar um ponto de interrogação na caixa de mensagem. A definição de `MB_ICONQUESTION` está em WinUser. h e aparece da seguinte maneira:  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3. Adicione instruções `Const` equivalentes à sua classe ou módulo para tornar essas constantes disponíveis para seu aplicativo. Por exemplo:  
  
     [!code-vb[VbVbalrInterop#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#11)]  
  
###### <a name="to-call-the-dll-procedure"></a>Para chamar o procedimento de DLL  
  
1. Adicione um botão chamado `Button1` ao formulário de inicialização para seu projeto e clique duas vezes nele para exibir seu código. O manipulador de eventos para o botão é exibido.  
  
2. Adicione código ao manipulador de eventos `Click` para o botão que você adicionou, para chamar o procedimento e fornecer os argumentos apropriados:  
  
     [!code-vb[VbVbalrInterop#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#12)]  
  
3. Execute o projeto pressionando F5. A caixa de mensagem é exibida com os botões **Sim** e **não** de resposta. Clique em um deles.  
  
#### <a name="data-marshaling"></a>Marshaling de dados  
 Visual Basic converte automaticamente os tipos de dados de parâmetros e valores de retorno para chamadas à API do Windows, mas você pode usar o atributo `MarshalAs` para especificar explicitamente os tipos de dados não gerenciados esperados por uma API. Para obter mais informações sobre o marshaling de interoperabilidade, consulte [marshaling interop](../../../framework/interop/interop-marshaling.md).  
  
##### <a name="to-use-declare-and-marshalas-in-an-api-call"></a>Para usar declare e MarshalAs em uma chamada à API  
  
1. Determine o nome da função que você deseja chamar, além de seus argumentos, tipos de dados e valor de retorno.  
  
2. Para simplificar o acesso ao atributo `MarshalAs`, adicione uma instrução `Imports` à parte superior do código para a classe ou módulo, como no exemplo a seguir:  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
3. Adicione um protótipo de função para a função importada à classe ou módulo que você está usando e aplique o atributo `MarshalAs` para os parâmetros ou valor de retorno. No exemplo a seguir, uma chamada à API que espera que o tipo `void*` seja empacotada como `AsAny`:  
  
     [!code-vb[VbVbalrInterop#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#14)]  
  
## <a name="api-calls-using-dllimport"></a>Chamadas de API usando DllImport  
 O atributo `DllImport` fornece uma segunda maneira de chamar funções em DLLs sem bibliotecas de tipos. `DllImport` é aproximadamente equivalente a usar uma instrução `Declare`, mas fornece mais controle sobre como as funções são chamadas.  
  
 Você pode usar `DllImport` com a maioria das chamadas à API do Windows, desde que a chamada se refira a um método compartilhado (às vezes chamado de *estático*). Você não pode usar métodos que exigem uma instância de uma classe. Ao contrário de instruções `Declare`, `DllImport` chamadas não podem usar o atributo `MarshalAs`.  
  
### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a>Para chamar uma API do Windows usando o atributo DllImport  
  
1. Abra um novo projeto de aplicativo do Windows clicando em **novo** no menu **arquivo** e, em seguida, clicando em **projeto**. A caixa de diálogo **Novo Projeto** é exibida.  
  
2. Selecione **aplicativo do Windows** na lista de modelos de projeto Visual Basic. O novo projeto é exibido.  
  
3. Adicione um botão chamado `Button2` ao formulário de inicialização.  
  
4. Clique duas vezes em `Button2` para abrir o modo de exibição de código para o formulário.  
  
5. Para simplificar o acesso ao `DllImport`, adicione uma instrução `Imports` à parte superior do código para a classe do formulário de inicialização:  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
6. Declare uma função vazia que precede a instrução `End Class` para o formulário e nomeie a função `MoveFile`.  
  
7. Aplique os modificadores `Public` e `Shared` à declaração de função e defina parâmetros para `MoveFile` com base nos argumentos que a função da API do Windows usa:  
  
     [!code-vb[VbVbalrInterop#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#16)]  
  
     Sua função pode ter qualquer nome de procedimento válido; o atributo `DllImport` especifica o nome na DLL. Ele também lida com o marshaling de interoperabilidade para os parâmetros e valores de retorno, de modo que você pode escolher os tipos de dados do Visual Studio que são semelhantes aos tipos de dados usados pela API.  
  
8. Aplique o atributo `DllImport` à função Empty. O primeiro parâmetro é o nome e o local da DLL que contém a função que você está chamando. Você não precisa especificar o caminho para os arquivos localizados nos diretórios de sistema do Windows. O segundo parâmetro é um argumento nomeado que especifica o nome da função na API do Windows. Neste exemplo, o atributo `DllImport` força chamadas a `MoveFile` para serem encaminhadas para `MoveFileW` em KERNEL32. DLL. O método `MoveFileW` copia um arquivo do caminho `src` para o caminho `dst`.  
  
     [!code-vb[VbVbalrInterop#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#17)]  
  
9. Adicione código ao manipulador de eventos `Button2_Click` para chamar a função:  
  
     [!code-vb[VbVbalrInterop#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#18)]  
  
10. Crie um arquivo chamado Test. txt e coloque-o no diretório C:\Tmp no seu disco rígido. Crie o diretório tmp, se necessário.  
  
11. Pressione F5 para iniciar o aplicativo. O formulário principal é exibido.  
  
12. Clique em **Button2**. A mensagem "o arquivo foi movido com êxito" será exibida se o arquivo puder ser movido.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [Alias](../../../visual-basic/language-reference/statements/alias-clause.md)
- [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Criando protótipos em código gerenciado](../../../framework/interop/creating-prototypes-in-managed-code.md)
- [Realizando marshaling de um delegado como um método de retorno de chamada](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)
