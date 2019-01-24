---
title: 'Passo a passo: Chamando APIs do Windows (Visual Basic)'
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
ms.openlocfilehash: 59c316ccb3a35a650ac11b96717a3ad729e777a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657968"
---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a>Passo a passo: Chamando APIs do Windows (Visual Basic)
APIs do Windows são bibliotecas de vínculo dinâmico (DLLs) que fazem parte do sistema operacional Windows. Você pode usá-los para executar tarefas quando é difícil escrever procedimentos equivalentes de sua preferência. Por exemplo, o Windows fornecem uma função chamada `FlashWindowEx` que permite que você faça a barra de título para um aplicativo alternativo entre tonalidades claras e escuras.  
  
 A vantagem de usar as APIs do Windows em seu código é que elas podem economizar tempo de desenvolvimento, porque eles contêm dezenas de funções úteis que já foram criadas e esperando para ser usado. A desvantagem é que as APIs do Windows pode ser difícil trabalhar com e implacável quando as coisas dão errado.  
  
 APIs do Windows representam uma categoria especial de interoperabilidade. APIs do Windows não use código gerenciado, não têm interno bibliotecas de tipos e usar os tipos de dados que são diferentes daqueles usados com o Visual Studio. Devido a essas diferenças, e como as APIs do Windows não são objetos COM, interoperabilidade com APIs do Windows e o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] é realizada usando a plataforma de invocar, ou PInvoke. Invocação de plataforma é um serviço que permite que código gerenciado chame funções não gerenciadas implementadas em DLLs. Para obter mais informações, consulte [consumindo funções de DLL não gerenciadas](../../../framework/interop/consuming-unmanaged-dll-functions.md). Você pode usar PInvoke no Visual Basic usando o `Declare` instrução ou aplicar o `DllImport` de atributo a um procedimento vazio.  
  
 Chamadas à API do Windows foram uma parte importante do Visual Basic de programação no passado, mas raramente são necessárias com o Visual Basic .NET. Sempre que possível, você deve usar código gerenciado do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] para executar tarefas, em vez de chamadas à API do Windows. Este passo a passo fornece informações sobre as situações nas quais o uso APIs do Windows é necessária.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a>Chamadas de API usando Declare  
 A maneira mais comum de chamar APIs do Windows é usando o `Declare` instrução.  
  
#### <a name="to-declare-a-dll-procedure"></a>Para declarar um procedimento DLL  
  
1.  Determine o nome da função que você deseja chamar, além de seus argumentos, tipos de argumento e retornam o valor, bem como o nome e local da DLL que o contém.  
  
    > [!NOTE]
    >  Para obter informações completas sobre as APIs do Windows, consulte a documentação do SDK do Win32 na plataforma SDK do Windows API. Para obter mais informações sobre as constantes que usam APIs do Windows, examine os arquivos de cabeçalho, como Windows. h incluído com o SDK de plataforma.  
  
2.  Abra um novo projeto de aplicativo do Windows clicando **New** sobre o **arquivo** menu e, em seguida, clicando em **projeto**. A caixa de diálogo **Novo Projeto** é exibida.  
  
3.  Selecione **aplicativo do Windows** da lista de modelos de projeto do Visual Basic. O novo projeto é exibido.  
  
4.  Adicione o seguinte `Declare` para a classe ou módulo no qual você deseja usar a DLL de função:  
  
     [!code-vb[VbVbalrInterop#9](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_1.vb)]  
  
### <a name="parts-of-the-declare-statement"></a>Partes da instrução Declare  
 O `Declare` instrução inclui os seguintes elementos.  
  
#### <a name="auto-modifier"></a>Modificador auto  
 O `Auto` modificador instrui o tempo de execução para converter a cadeia de caracteres com base no nome do método de acordo com regras de tempo de execução de linguagem comum (ou nome de alias se especificado).  
  
#### <a name="lib-and-alias-keywords"></a>Palavras-chave lib e Alias  
 O nome após o `Function` palavra-chave é o nome do seu programa usa para acessar a função importada. Ele pode ser o mesmo que o nome real da função que você está chamando, ou você pode usar qualquer nome válido de procedimento e, em seguida, empregar o `Alias` palavra-chave para especificar o nome real da função que você está chamando.  
  
 Especifique o `Lib` palavra-chave, seguido do nome e local da DLL que contém a função que você está chamando. Você não precisa especificar o caminho para arquivos localizados em pastas do sistema Windows.  
  
 Use o `Alias` palavra-chave se o nome da função que você está chamando não é um nome válido de procedimento do Visual Basic ou está em conflito com o nome de outros itens em seu aplicativo. `Alias` indica o nome da função que está sendo chamado.  
  
#### <a name="argument-and-data-type-declarations"></a>Argumento e declarações de tipo de dados  
 Declare os argumentos e seus tipos de dados. Esta parte pode ser desafiador porque os tipos de dados que usa o Windows não correspondem aos tipos de dados do Visual Studio. Visual Basic faz uma grande parte do trabalho ao converter argumentos para tipos de dados compatíveis, um processo chamado *marshaling*. Você pode controlar explicitamente como argumentos são empacotados usando o <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributo definido no <xref:System.Runtime.InteropServices> namespace.  
  
> [!NOTE]
>  As versões anteriores do Visual Basic permitiam que você declarar parâmetros `As Any`, significando que dados de qualquer dado de tipo pode ser usado. Visual Basic exige que você use um tipo de dados específico para todos os `Declare` instruções.  
  
#### <a name="windows-api-constants"></a>Constantes de API do Windows  
 Alguns argumentos são combinações de constantes. Por exemplo, o `MessageBox` API mostrada neste passo a passo aceita um argumento de inteiro chamado `Typ` que controla como a caixa de mensagem é exibida. Você pode determinar o valor numérico de constantes examinando o `#define` instruções no arquivo WinUser. H. Os valores numéricos geralmente são mostrados em hexadecimal, portanto, você talvez queira usar uma calculadora para adicioná-los e converter em decimal. Por exemplo, se você desejar combinar as constantes para o estilo de exclamação `MB_ICONEXCLAMATION` 0x00000030 e Sim/não estilo `MB_YESNO` 0x00000004, você pode adicionar os números e obter um resultado de 0x00000034, ou 52 decimal. Embora você possa usar o resultado decimal diretamente, é melhor declarar esses valores como constantes em seu aplicativo e combiná-los usando o `Or` operador.  
  
###### <a name="to-declare-constants-for-windows-api-calls"></a>Para declarar constantes para chamadas à API do Windows  
  
1.  Consulte a documentação para a função do Windows que você está chamando. Determine o nome de constantes que são usadas e o nome do arquivo. h que contém os valores numéricos para constantes.  
  
2.  Use um editor de texto, como o bloco de notas, para exibir o conteúdo do arquivo de cabeçalho (. h) e localizar os valores associados com as constantes que você está usando. Por exemplo, o `MessageBox` API usa a constante `MB_ICONQUESTION` para mostrar um ponto de interrogação na caixa de mensagem. A definição para `MB_ICONQUESTION` está em winuser. H e aparece da seguinte maneira:  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3.  Adicionar equivalente `Const` instruções à sua classe ou módulo para tornar essas constantes disponíveis para seu aplicativo. Por exemplo:  
  
     [!code-vb[VbVbalrInterop#11](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_2.vb)]  
  
###### <a name="to-call-the-dll-procedure"></a>Para chamar o procedimento DLL  
  
1.  Adicionar um botão chamado `Button1` na inicialização de formulário para o seu projeto e, em seguida, clique duas vezes nele para exibir seu código. O manipulador de eventos para o botão é exibido.  
  
2.  Adicione código para o `Click` manipulador de eventos para o botão é adicionado, para chamar o procedimento e forneça os argumentos apropriados:  
  
     [!code-vb[VbVbalrInterop#12](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_3.vb)]  
  
3.  Execute o projeto pressionando F5. A caixa de mensagem é exibida com as duas **Yes** e **não** botões de resposta. Clique em qualquer um.  
  
#### <a name="data-marshaling"></a>Marshaling de dados  
 Visual Basic converte automaticamente os tipos de dados de parâmetros e valores de retorno para chamadas à API do Windows, mas você pode usar o `MarshalAs` atributo para especificar explicitamente os tipos de dados não gerenciados que esperam uma API. Para obter mais informações sobre o marshaling de interoperabilidade, consulte [Marshaling de interoperabilidade](../../../framework/interop/interop-marshaling.md).  
  
###### <a name="to-use-declare-and-marshalas-in-an-api-call"></a>Para usar Declare e MarshalAs em uma chamada à API  
  
1.  Determinar o nome da função que você deseja chamar, além de seus argumentos, tipos de dados, e o valor de retorno.  
  
2.  Para simplificar o acesso para o `MarshalAs` do atributo, adicione um `Imports` instrução na parte superior do código para a classe ou módulo, como no exemplo a seguir:  
  
     [!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
3.  Adicionar um protótipo de função para a função importada para a classe ou módulo que você está usando e se aplicam a `MarshalAs` aos parâmetros de atributo ou valor de retorno. No exemplo a seguir, uma chamada à API que o tipo de espera `void*` é empacotado como `AsAny`:  
  
     [!code-vb[VbVbalrInterop#14](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_5.vb)]  
  
## <a name="api-calls-using-dllimport"></a>Chamadas de API usando DllImport  
 O `DllImport` atributo fornece uma segunda maneira para chamar funções em DLLs sem bibliotecas de tipos. `DllImport` é aproximadamente equivalente a usar um `Declare` instrução, mas oferece mais controle sobre como as funções são chamadas.  
  
 Você pode usar `DllImport` com a API do Windows a maioria das chamadas, desde a chamada se refere a um compartilhado (às vezes chamado de *estático*) método. Você não pode usar os métodos que exigem uma instância de uma classe. Diferentemente `Declare` instruções `DllImport` chamadas não é possível usar o `MarshalAs` atributo.  
  
#### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a>Chamar uma API do Windows usando o atributo DllImport  
  
1.  Abra um novo projeto de aplicativo do Windows clicando **New** sobre o **arquivo** menu e, em seguida, clicando em **projeto**. A caixa de diálogo **Novo Projeto** é exibida.  
  
2.  Selecione **aplicativo do Windows** da lista de modelos de projeto do Visual Basic. O novo projeto é exibido.  
  
3.  Adicionar um botão chamado `Button2` para o formulário de inicialização.  
  
4.  Clique duas vezes em `Button2` para abrir a exibição de código para o formulário.  
  
5.  Para simplificar o acesso aos `DllImport`, adicione um `Imports` instrução na parte superior do código para a classe de formulário de inicialização:  
  
     [!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
6.  Declarar uma função vazia anterior a `End Class` instrução para o formulário e nomeie a função `MoveFile`.  
  
7.  Aplicar a `Public` e `Shared` modificadores de declaração de função e definir parâmetros para `MoveFile` com base nos argumentos que usa a função da API do Windows:  
  
     [!code-vb[VbVbalrInterop#16](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_6.vb)]  
  
     Sua função pode ter qualquer nome válido de procedimento; o `DllImport` atributo especifica o nome na DLL. Ele também lida com marshaling de interoperabilidade para os parâmetros e a API usa tipos de valores de retorno, portanto, você pode escolher os tipos de dados do Visual Studio que são semelhantes aos dados.  
  
8.  Aplicar o `DllImport` atributo à função vazia. O primeiro parâmetro é o nome e local da DLL que contém a função que você está chamando. Você não precisa especificar o caminho para arquivos localizados em pastas do sistema Windows. O segundo parâmetro é um argumento nomeado que especifica o nome da função na API do Windows. Neste exemplo, o `DllImport` força chamadas para o atributo `MoveFile` sejam encaminhadas ao `MoveFileW` em KERNEL32. DLL. O `MoveFileW` método copia um arquivo do caminho `src` para o caminho `dst`.  
  
     [!code-vb[VbVbalrInterop#17](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_7.vb)]  
  
9. Adicione código para o `Button2_Click` manipulador de eventos para chamar a função:  
  
     [!code-vb[VbVbalrInterop#18](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_8.vb)]  
  
10. Crie um arquivo chamado Test. txt e coloque-na pasta C:\Tmp em seu disco rígido. Se necessário, crie a pasta Tmp.  
  
11. Pressione F5 para iniciar o aplicativo. O formulário principal é exibida.  
  
12. Clique em **Button2**. A mensagem "o arquivo foi movido com êxito" será exibida se o arquivo pode ser movido.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Runtime.InteropServices.DllImportAttribute>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [Alias](../../../visual-basic/language-reference/statements/alias-clause.md)
- [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Criando protótipos em código gerenciado](../../../framework/interop/creating-prototypes-in-managed-code.md)
- [Realizando marshaling de um delegado como um método de retorno de chamada](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)
