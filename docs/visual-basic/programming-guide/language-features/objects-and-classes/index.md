---
title: "Objetos e classes no Visual Basic | Microsoft Docs"
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
  - "classes [Visual Basic]"
  - "objetos [Visual Basic]"
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
caps.latest.revision: 26
caps.handback.revision: 26
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Objetos e classes no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Um  *objeto* é uma combinação de código e dados que podem ser tratados como uma unidade.  Um objeto pode ser uma parte de um aplicativo, como um controle ou formulário.  Todo o aplicativo também pode ser um objeto.  
  
 Quando você cria um aplicativo no [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], você constantemente trabalha com objetos.  Você pode usar objetos fornecidos pela [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], como controles, formulários e objetos de acesso a dados.  Você também pode usar objetos de outros aplicativos em seu aplicativo [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] .  Você pode até mesmo criar seus próprios objetos e definir propriedades e métodos adicionais para eles.  Objetos atuam como blocos pré\-fabricadosde construção para programas — eles permitem que você escrever uma parte de código uma vez e reutilizá\-lo repetidamente.  
  
 Este tópico discute os objetos em detalhes.  
  
## Objetos e classes  
 Cada objeto no [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] é definido por um  *classe*.  Uma classe descreve as variáveis, propriedades, procedimentos e eventos de um objeto.  Objetos são instâncias de classes; Você pode criar quantos objetos que você precisa depois de ter definido uma classe.  
  
 Para entender a relação entre um objeto e sua classe, pense cutters cookie e cookies.  O cortador é a classe.  Ele define as características de cada cookie, por exemplo, tamanho e forma.  A classe é usada para criar objetos.  Os objetos são os cookies.  
  
 Você deve criar um objeto antes de acessar seus membros.  
  
#### Para criar um objeto de uma classe  
  
1.  Determine de qual classe você deseja criar um objeto.  
  
2.  Escreva uma [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) para criar uma variável à qual você pode designar uma instância de classe.  A variável deve ser do tipo da classe desejada.  
  
    ```  
  
    Dim nextCustomer As customer   
    ```  
  
3.  Adicione a palavra\-chave [Operador New](../../../../visual-basic/language-reference/operators/new-operator.md) para inicializar a variável a uma nova instância da classe.  
  
    ```  
    Dim nextCustomer As New customer  
    ```  
  
4.  Você pode agora acessar os membros da classe através da variável de objeto.  
  
    ```  
  
    nextCustomer.accountNumber = lastAccountNumber + 1  
    ```  
  
> [!NOTE]
>  Quando possível, você deve declarar a variável para ser do tipo de classe que você pretende designar\-lhe.  Isso é chamado *associação inicial*.  Se você não sabe o tipo de classe no momento de compilação, você pode invocar *associação tardia* declarando a variável para ser do [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md).  Entretanto, a associação tardia pode fazer o desempenho ficar mais lento e limitar acesso aos membros de objeto de tempo de execução.  Para mais informações, consulte [Declaração de variável do objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).  
  
### Várias instâncias  
 Objetos criados recentemente de uma classe geralmente são idênticos entre si.  Depois que eles existem como objetos individuais, Entretanto, suas propriedades e variáveis podem ser alteradas independentemente das outras instâncias.  Por exemplo, se você adicionar três caixas de seleção a um formulário, cada objeto de caixa de seleção é uma instância de <xref:System.Windows.Forms.CheckBox> classe.  O indivíduo <xref:System.Windows.Forms.CheckBox> objetos compartilham um conjunto comum de características e recursos \(Propriedades, variáveis, procedimentos e eventos\) definidos pela classe.  No entanto, cada um tem seu próprio nome, pode ser separadamente ativada e desabilitada e podem ser colocados em um local diferente no formulário.  
  
## Membros do objeto  
 Um objeto é um elemento de um aplicativo, que representa uma  *instância* de uma classe.  Campos, propriedades, métodos e eventos são os blocos de construção de objetos e constituem seus  *membros da*.  
  
### Acesso de membro  
 Acessar um membro de um objeto, especificando, em ordem, o nome da variável de objeto, um período \(`.`\) e o nome do membro.  O exemplo seguinte define o <xref:System.Windows.Forms.Control.Text%2A> propriedade de um <xref:System.Windows.Forms.Label> objeto.  
  
```  
warningLabel.Text = "Data not saved"  
```  
  
#### IntelliSense lista de membros  
 IntelliSense lista os membros de uma classe quando você chamar sua opção de membros da lista, por exemplo, quando você digitar um ponto \(`.`\) como um operador de acesso de membro.  Se você digitar o período após o nome de uma variável declarada como uma instância dessa classe, IntelliSense lista todos os membros de instância e nenhum dos membros compartilhados.  Se você digitar o ponto após o nome da classe, IntelliSense lista todos os membros compartilhados e nenhum dos membros de instância.  Para mais informações, consulte [Usando IntelliSense](/visual-studio/ide/using-intellisense).  
  
### Campos e propriedades  
 *Campos* e  *Propriedades* representam as informações armazenadas em um objeto.  Recuperar e definir seus valores com instruções de atribuição da mesma forma, recuperar e definir variáveis locais em um procedimento.  O exemplo a seguir recupera o <xref:System.Windows.Forms.Control.Width%2A> propriedade e conjuntos de <xref:System.Windows.Forms.Control.ForeColor%2A> propriedade de um <xref:System.Windows.Forms.Label> objeto.  
  
```  
Dim warningWidth As Integer = warningLabel.Width  
warningLabel.ForeColor = System.Drawing.Color.Red  
```  
  
 Observe que também é chamado de um campo de um  *variável de membro*.  
  
 Use os procedimentos de propriedade quando:  
  
-   Você precisa controlar quando e como um valor é definido ou recuperado.  
  
-   A propriedade tem um conjunto bem definido de valores que precisam ser validados.  
  
-   A definição do valor causa alguma alteração perceptível no estado do objeto, como um `IsVisible` propriedade.  
  
-   A configuração da propriedade faz alterações para outras variáveis internas ou os valores de outras propriedades.  
  
-   Um conjunto de etapas deve ser executado antes que a propriedade pode ser definida ou recuperada.  
  
 Use campos quando:  
  
-   O valor é de um tipo de autovalidado.  Por exemplo, um erro ou uma conversão automática de dados ocorre se um valor diferente de `True` ou `False` é atribuído a uma `Boolean` variável.  
  
-   Qualquer valor no intervalo suportado pelo tipo de dados é válido.  Isso é verdadeiro de muitas propriedades do tipo `Single` ou `Double`.  
  
-   A propriedade é um `String` tipo de dados, e não há nenhuma restrição de tamanho ou valor da seqüência.  
  
-   Para mais informações, consulte [Procedimentos de propriedade](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).  
  
### Métodos  
 A  *método* é uma ação que um objeto pode executar.  Por exemplo, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> é um método de <xref:System.Windows.Forms.ComboBox> objeto adiciona uma nova entrada para uma caixa de combinação.  
  
 O exemplo a seguir demonstra a <xref:System.Windows.Forms.Timer.Start%2A> método de um <xref:System.Windows.Forms.Timer> objeto.  
  
```  
Dim safetyTimer As New System.Windows.Forms.Timer  
safetyTimer.Start()  
```  
  
 Observe que um método é simplesmente um  *procedimento* que é exposto por um objeto.  
  
 Para mais informações, consulte [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md).  
  
### Eventos  
 Um evento é uma ação reconhecida por um objeto, como clicar o mouse ou pressionando uma tecla e para o qual você pode escrever código para responder.  Os eventos podem ocorrer como resultado de uma ação do usuário ou o código de programa, ou pode ser causados pelo sistema.  Código que sinaliza um evento é considerado  *Elevar* o evento e o código que responde a ele é considerado  *manipular* \-lo.  
  
 Você também pode desenvolver seus próprios eventos personalizados a ser gerado por seus objetos e manipulados por outros objetos.  Para mais informações, consulte [Eventos](../../../../visual-basic/programming-guide/language-features/events/events.md).  
  
### Membros de instância e compartilhado  
 Quando você cria um objeto de uma classe, o resultado é uma instância dessa classe.  Membros que não são declarados com o [Compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md) palavra\-chave  *membros de instância*, que estritamente pertencem a essa instância em particular.  Um membro de instância em uma instância é independente do mesmo membro em outra instância da mesma classe.  Uma variável de membro de instância, por exemplo, pode ter valores diferentes em diferentes instâncias.  
  
 Membros declarados com o `Shared` palavra\-chave  *membros compartilhados*, que pertencem à classe como um todo e não para qualquer instância específica.  Um membro compartilhado existe somente uma vez, não importa quantas instâncias de sua classe que você criar ou mesmo se você criar sem instâncias.  Uma variável de membro compartilhado, por exemplo, tem apenas um valor, que está disponível para todo o código pode acessar a classe.  
  
#### Acessando Membros Não Compartilhados  
  
###### Para acessar um membro não compartilhado de um objeto  
  
1.  Certifique\-se que o objeto foij sido criado a partir de sua classe e atribuído a um variável de objeto.  
  
    ```  
    Dim secondForm As New System.Windows.Forms.Form  
    ```  
  
2.  Na declaração que acessa o membro, siga o nome da variável de objeto com o *operador de acesso a membro*\(`.`\) e em seguida com o nome.  
  
    ```  
    secondForm.Show()  
    ```  
  
#### Acessando membros compartilhados  
  
###### Para acessar um membro compartilhado de um objeto  
  
-   Siga o nome da classe com o *operador de acesso a membro* \(`.`\) e o nome do membro.  Você sempre deve acessar um membro `Shared` do objeto diretamente através do nome da classe.  
  
    ```  
    MsgBox("This computer is called " & Environment.MachineName)  
    ```  
  
-   Se você já tiver criado um objeto da classe, você também pode acessar um membro `Shared` através da variável do objeto.  
  
### Diferenças entre classes e módulos  
 A principal diferença entre classes e módulos é que as classes podem ser instanciadas como objetos enquanto os módulos padrão não podem.  Como há apenas uma cópia dos dados de um módulo padrão, quando uma parte do seu programa altera uma variável pública em um módulo padrão, qualquer outra parte do programa recebe o mesmo valor se ler essa variável.  Em contraste, dados do objeto existem separadamente para cada objeto instanciado.  Outra diferença é que, ao contrário dos módulos padrão, classes podem implementar interfaces.  
  
> [!NOTE]
>  Quando o modificador `Shared` é aplicado a um membro de classe, ele está associado com a classe em si em vez de uma determinada instância da classe.  O membro é acessado diretamente usando o nome da classe, da mesma maneira que membros de módulo são acessados.  
  
 Classes e módulos também usam escopos diferentes para seus membros.  Membros definidos em uma classe têm escopo em uma instância específica da classe e existem apenas durante a vida útil do objeto.  Para acessar membros de classe de fora de uma classe, você deve usar nomes totalmente qualificados no formato de *Objeto*.*Membro*.  
  
 Por outro lado, o membros declarados dentro de um módulo são acessíveis publicamente por padrão e podem ser acessados por qualquer código que pode acessar o módulo.  Isso significa que variáveis em um módulo padrão são na realidade variáveis globais, pois estão visíveis de qualquer lugar em seu projeto, e existem durante a vida útil do programa.  
  
## Reutilização de objetos e Classes  
 Objetos permitem que você declarar variáveis e procedimentos de uma vez e reutilizá\-los sempre que necessário.  Por exemplo, se você deseja adicionar um verificador ortográfico para um aplicativo pode definir todas as variáveis e suporte a funções para fornecer a funcionalidade de verificação ortográfica.  Se você criar seu verificador ortográfico como uma classe, você pode, em seguida, reutilizá\-lo em outros aplicativos adicionando uma referência ao assembly compilado.  Melhor ainda, você poderá economizar algum trabalho usando uma classe do verificador ortográfico que alguém já desenvolveu.  
  
 O [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] fornece muitos exemplos de componentes que estão disponíveis para uso.  O exemplo a seguir usa o <xref:System.TimeZone> de classe na <xref:System> namespace.  <xref:System.TimeZone>fornece a membros que permitem recuperar informações sobre o fuso horário do sistema do computador atual.  
  
```  
Public Sub examineTimeZone()  
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone  
    Dim s As String = "Current time zone is "  
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "  
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "  
    s &= "different from UTC (coordinated universal time)"  
    s &= vbCrLf & "and is currently "  
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "  
    s &= "on ""summer time""."  
    MsgBox(s)  
End Sub  
```  
  
 No exemplo anterior, o primeiro [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) declara uma variável de objeto do tipo <xref:System.TimeZone> e atribui a ele um <xref:System.TimeZone> objeto retornado pela <xref:System.TimeZone.CurrentTimeZone%2A> propriedade.  
  
## Relações Entre Objetos  
 Objetos podem estar relacionados a si de várias maneiras.  Os principais tipos de relação são *hierarchical* e  *confinamento* .  
  
### Relação hierárquica  
 Quando classes são derivadas de classes mais fundamentais, eles são dizemos têm uma relação hierárquica .  Hierarquias de classe são úteis para descrever itens que estão um subtipo de uma classe mais geral.  
  
 No exemplo a seguir, suponha que você deseje definir um tipo especial de <xref:System.Windows.Forms.Button> que atua como um <xref:System.Windows.Forms.Button> normal, mas também expõe um método que reverte as cores de primeiro plano e plano de fundo.  
  
##### Para definir uma classe é derivada de uma classe já existente  
  
1.  Use um [Instrução Class](../../../../visual-basic/language-reference/statements/class-statement.md) para definir uma classe a partir da qual criar o objeto que você precisa.  
  
     `Public Class reversibleButton`  
  
     Esteja certo de que uma declaração `End Class` segue a última linha do código em sua classe.  Por padrão, a ambiente de desenvolvimento integrado \(IDE\) gera automaticamente um `End Class` quando você insere uma declaração `Class` .  
  
2.  Siga a declaração `Class` imediatamente com uma [Instrução Inherits](../../../../visual-basic/language-reference/statements/inherits-statement.md).  Especifique a classe da qual a nova classe deriva.  
  
     `Inherits System.Windows.Forms.Button`  
  
     A nova classe herda todos os membros definidos pela classe base.  
  
3.  Adicione o código para os membros adicionais que sua classe derivada expõe.  Por exemplo, você pode adicionar um método `reverseColors`, e a classe derivada pode parecer como a seguir:  
  
    ```  
    Public Class reversibleButton  
        Inherits System.Windows.Forms.Button  
        Public Sub reverseColors()   
            Dim saveColor As System.Drawing.Color = Me.BackColor  
            Me.BackColor = Me.ForeColor  
            Me.ForeColor = saveColor  
        End Sub  
    End Class   
    ```  
  
     Se você criar um objeto da classe `reversibleButton`, ele pode acessar todos os membros da classe <xref:System.Windows.Forms.Button>, bem como o método `reverseColors` e quaisquer outros novos membros que você definir na `reversibleButton`.  
  
 Classes derivadas herdam os membros da classe que eles se baseiam, permitindo que você adicionar complexidade como você progresso em uma hierarquia de classe.  Para mais informações, consulte [Noções básicas de herança](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
#### Compilando o código  
 Esteja certo de que o compilador pode acessar a classe da qual você pretende derivar sua nova classe.  Isso pode significar qualificar totalmente seu nome, como no exemplo anterior, ou identificar seu espaço de nomes em um [Instrução Imports \(tipo e namespace .NET\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  Se a classe está em um projeto diferente, você talvez precise adicionar uma referência ao projeto.  Para mais informações, consulte [Gerenciando referências em um projeto](/visual-studio/ide/managing-references-in-a-project).  
  
### Relacionamento de contenção  
 Outra maneira que os objetos podem estar relacionados é um relacionamento de confinamento .  Objetos de recipiente encapsulam logicamente outros objetos.  Por exemplo, o objeto <xref:System.OperatingSystem> logicamente contém um objeto <xref:System.Version>, que ela retorna a sua propriedade <xref:System.OperatingSystem.Version%2A>.  Observe que o objeto recipiente não fisicamente contém qualquer outro objeto.  
  
#### Coleções  
 Um tipo específico de confinamento de objeto é representado por  *coleções* .  Coleções são grupos de objetos semelhantes que podem ser enumerados.  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]oferece suporte a uma sintaxe específica na [Instrução For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) que permite que você iterar em itens de uma coleção.  Além disso, coleções com freqüência permitem usar um <xref:Microsoft.VisualBasic.Collection.Item%2A> para recuperar elementos pelo índice ou associando\-os a uma cadeia de caracteres exclusiva.  Coleções podem ser mais fácil de usar que matrizes porque elas permitem que você deseja adicionar ou remover itens sem usar índices.  Por causa das sua facilidade de uso, coleções são usadas para armazenar formulários e controles.  
  
## Tópicos relacionados  
 [Instruções passo a passo: definindo classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)  
 Fornece uma descrição passo a passo sobre como criar uma classe.  
  
 [Propriedades e métodos sobrecarregados](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)  
 Propriedades e métodos sobrecarregados  
  
 [Noções básicas de herança](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 Aborda modificadores de herança, substituindo métodos e propriedades, MyClass e MyBase.  
  
 [Tempo de vida do objeto: como os objetos são criados e destruídos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 Aborda a criação e eliminação de instâncias de classe.  
  
 [Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 Descreve como criar e usar tipos anônimos, que permitem que você crie objetos sem escrever uma definição de classe para o tipo de dados.  
  
 [Inicializadores de objeto: tipos nomeados e anônimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)  
 Discute inicializadores de objeto, que são usados para criar instâncias dos tipos anônimo e nomeado usando uma única expressão.  
  
 [Como inferir nomes e tipos de propriedade na declaração de tipo anônimo](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 Explica como inferir nomes de propriedade e tipos nas declarações anônimas de tipo.  Fornece exemplos de inferência bem\-sucedidas e malsucedida.