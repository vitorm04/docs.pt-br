---
title: "Passo a passo: Criando e usando objetos din&#226;micos (C# e Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "objetos dinâmicos"
  - "objetos dinâmicos [C#]"
  - "objetos dinâmicos [Visual Basic]"
ms.assetid: 568f1645-1305-4906-8625-5d77af81e04f
caps.latest.revision: 22
caps.handback.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Passo a passo: Criando e usando objetos din&#226;micos (C# e Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Os objetos dinâmicos membros expostos como propriedades e métodos em tempo de execução, em vez de em tempo de compilação.  Isso permite que você crie objetos para trabalhar com estruturas que não correspondem um tipo ou um formato estático.  Por exemplo, você pode usar um objeto dinâmico para fazer referência ao modelo de objeto \(DOM\) do documento HTML, que pode conter qualquer combinação de elementos e atributos válidos de marcação HTML.  Porque cada documento HTML é exclusivo, os membros para um documento HTML de detalhes são determinados em tempo de execução.  Um método comum para fazer referência a um atributo de um elemento HTML é passar o nome do atributo para o método de `GetProperty` do elemento.  Para fazer referência ao atributo de `id` do elemento HTML `<div id="Div1">`, você primeiro obtenha uma referência ao elemento de `<div>` e em seguida, usa `divElement.GetProperty("id")`.  Se você usar um objeto dinâmico, você pode referenciar o atributo de `id` como `divElement.id`.  
  
 Os objetos dinâmicos também fornecem acesso conveniente às linguagens dinâmicos como IronPython e IronRuby.  Você pode usar um objeto dinâmico para se referir a um script dinâmico que é interpretado em tempo de execução.  
  
 Você referencia um objeto dinâmico usando associação tardia.  Em C\#, você especifica o tipo de um objeto de associação tardia como `dynamic`.  Em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], você especifica o tipo de um objeto de associação tardia como `Object`.  Para obter mais informações, consulte [dynamic](../../../csharp/language-reference/keywords/dynamic.md) e [Associação antecipada e tardia](../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md).  
  
 Você pode criar objetos dinâmicos personalizados usando as classes no namespace de <xref:System.Dynamic?displayProperty=fullName> .  Por exemplo, você pode criar <xref:System.Dynamic.ExpandoObject> e especificar os membros do objeto em tempo de execução.  Você também pode criar seu próprio tipo que herda da classe de <xref:System.Dynamic.DynamicObject> .  Você pode então substituir os membros da classe de <xref:System.Dynamic.DynamicObject> para fornecer o tempo de execução funcionalidade dinâmico.  
  
 Em essa explicação passo a passo você executará as seguintes tarefas:  
  
-   Crie um objeto personalizado que expõe dinamicamente o conteúdo de um arquivo de texto como propriedades de um objeto.  
  
-   Crie um projeto que usa uma biblioteca de `IronPython` .  
  
## Pré-requisitos  
 Você precisa IronPython 2.6.1 para .NET 4,0 para concluir esta explicação passo a passo.  você pode baixar IronPython 2.6.1 para .NET 4,0 de [CodePlex](http://go.microsoft.com/fwlink/?LinkId=187223).  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## criando um objeto dinâmico personalizado  
 O primeiro projeto que você criou em essa explicação passo a passo define um objeto dinâmico personalizado que procura o conteúdo de um arquivo de texto.  O texto a procurar pelo especificado pelo nome de uma propriedade dinâmica.  Por exemplo, se chamar o código especifica `dynamicFile.Sample`, a classe dinâmica retorna uma lista genérica de cadeias de caracteres que contém todas as linhas do arquivo que começam com “exemplo”.  A pesquisa não difere maiúsculas de minúsculas.  A classe dinâmica também suporta dois argumentos opcionais.  O primeiro argumento é um valor enum de opção de pesquisa que especifica que a classe dinâmica deve procurar por correspondências no início da linha, ao final da linha, ou em qualquer lugar na linha.  O segundo argumento especifica que a classe dinâmica deve ser preparada espaćamento e o espaço à esquerda de cada linha antes de procurar.  Por exemplo, se chamar o código especifica `dynamicFile.Sample(StringSearchOption.Contains)`, pesquisas dinâmicos da classe para “exemplo” em qualquer lugar em uma linha.  Se chamar o código especifica `dynamicFile.Sample(StringSearchOption.StartsWith, false)`, a classe dinâmica procura por exemplo “” no início de cada linha, e não remove ao primeiro e o espaço à direita.  O comportamento padrão da classe dinâmica é procurar por um correspondente no início de cada linha e remover ao primeiro e o espaço à direita.  
  
#### Para criar uma classe dinâmica personalizado  
  
1.  Inicie o [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]  
  
2.  No menu **File**, aponte para **New** e clique **Project**.  
  
3.  Em a caixa de diálogo de **Novo Projeto** , no painel de **Tipos de projeto** , certifique\-se que está selecionado **Janelas** .  **Aplicativo de Console** Selecione no painel de **Modelos** .  Em a caixa de **Nome** , o tipo `DynamicSample`, e clique em **OK**.  o novo projeto é criado.  
  
4.  Clique com o botão direito do mouse no projeto e o ponto de DynamicSample a **Adicionar**, clique em **Classe**.  Em a caixa de **Nome** , o tipo `ReadOnlyFile`, e clique em **OK**.  Um novo arquivo é adicionado que contém a classe de ReadOnlyFile.  
  
5.  Em a parte superior do arquivo de ReadOnlyFile.cs ou de ReadOnlyFile.vb, adicione o seguinte código para importar <xref:System.IO?displayProperty=fullName> e namespaces de <xref:System.Dynamic?displayProperty=fullName> .  
  
     [!code-cs[VbDynamicWalkthrough#1](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_1.cs)]
     [!code-vb[VbDynamicWalkthrough#1](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_1.vb)]  
  
6.  O objeto dinâmico usa um personalizado enum para determinar os critérios de pesquisa.  Antes da declaração de classe, adicione a seguinte definição enum.  
  
     [!code-cs[VbDynamicWalkthrough#2](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_2.cs)]
     [!code-vb[VbDynamicWalkthrough#2](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_2.vb)]  
  
7.  Atualizar a declaração de classe para herdar a classe de `DynamicObject` , conforme mostrado no exemplo de código a seguir.  
  
     [!code-cs[VbDynamicWalkthrough#3](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_3.cs)]
     [!code-vb[VbDynamicWalkthrough#3](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_3.vb)]  
  
8.  Adicione o seguinte código à classe de `ReadOnlyFile` para definir um campo particular para o caminho do arquivo e um construtor para a classe de `ReadOnlyFile` .  
  
     [!code-cs[VbDynamicWalkthrough#4](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_4.cs)]
     [!code-vb[VbDynamicWalkthrough#4](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_4.vb)]  
  
9. Adicione o seguinte método de `GetPropertyValue` a classe de `ReadOnlyFile` .  O método de `GetPropertyValue` aceita, como entrada, os critérios de pesquisa e retorna as linhas de um arquivo de texto que que correspondem critérios de pesquisa.  Métodos dinâmicos fornecido pela classe de `ReadOnlyFile` chama o método de `GetPropertyValue` para recuperar seus respectivos resultados.  
  
     [!code-cs[VbDynamicWalkthrough#5](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_5.cs)]
     [!code-vb[VbDynamicWalkthrough#5](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_5.vb)]  
  
10. Após o método de `GetPropertyValue` , adicione o seguinte código para substituir o método de <xref:System.Dynamic.DynamicObject.TryGetMember%2A> da classe de <xref:System.Dynamic.DynamicObject> .  O método de <xref:System.Dynamic.DynamicObject.TryGetMember%2A> é chamado quando um membro de uma classe dinâmica é solicitado e nenhum argumento é especificado.  O argumento de `binder` contém informações sobre o membro referenciado, e o argumento de `result` referencia o resultado retornado para o membro especificado.  O método de <xref:System.Dynamic.DynamicObject.TryGetMember%2A> retorna um valor Booleano que retorna `true` se o membro existe; aplicativo se não retorna `false`.  
  
     [!code-cs[VbDynamicWalkthrough#6](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_6.cs)]
     [!code-vb[VbDynamicWalkthrough#6](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_6.vb)]  
  
11. Após o método de `TryGetMember` , adicione o seguinte código para substituir o método de <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> da classe de <xref:System.Dynamic.DynamicObject> .  O método de <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> é chamado quando um membro de uma classe dinâmica é solicitado através de argumentos.  O argumento de `binder` contém informações sobre o membro referenciado, e o argumento de `result` referencia o resultado retornado para o membro especificado.  O argumento de `args` contém uma matriz de argumentos que são passados para o membro.  O método de <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> retorna um valor Booleano que retorna `true` se o membro existe; aplicativo se não retorna `false`.  
  
     A versão personalizada do método de `TryInvokeMember` espera que o primeiro argumento ser um valor enum de `StringSearchOption` que você definiu em uma etapa anterior.  o método de `TryInvokeMember` espera o segundo argumento ser um valor Booleano.  Se um ou ambos os argumento é valores válidos, eles são passados para o método de `GetPropertyValue` para recuperar os resultados.  
  
     [!code-cs[VbDynamicWalkthrough#7](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_7.cs)]
     [!code-vb[VbDynamicWalkthrough#7](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_7.vb)]  
  
12. Salve e feche o arquivo.  
  
#### Para criar um arquivo de texto de exemplo  
  
1.  Clique com o botão direito do mouse no projeto e o ponto de DynamicSample a **Adicionar**, clique em **Novo Item**.  Em o painel de **Modelos Instalados** , **Geral**selecione, e então selecione o modelo de **Arquivo de Texto** .  Deixe o nome padrão do TextFile1.txt na caixa de **Nome** , clique em **Adicionar**.  um novo arquivo de texto é adicionado ao projeto.  
  
2.  Copie o texto a seguir para o arquivo TextFile1.txt.  
  
    ```  
    List of customers and suppliers  
  
    Supplier: Lucerne Publishing (http://www.lucernepublishing.com/)  
    Customer: Preston, Chris  
    Customer: Hines, Patrick  
    Customer: Cameron, Maria  
    Supplier: Graphic Design Institute (http://www.graphicdesigninstitute.com/)   
    Supplier: Fabrikam, Inc. (http://www.fabrikam.com/)   
    Customer: Seubert, Roxanne  
    Supplier: Proseware, Inc. (http://www.proseware.com/)   
    Customer: Adolphi, Stephan  
    Customer: Koch, Paul  
    ```  
  
3.  Salve e feche o arquivo.  
  
#### Para criar um aplicativo de exemplo que usa o objeto dinâmico personalizado  
  
1.  Em **Gerenciador de Soluções**, clique duas vezes no arquivo Module1.vb se você estiver usando [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ou arquivo de Module.vb se você estiver usando o visual C\#.  
  
2.  Adicione o seguinte código ao procedimento principal para criar uma instância da classe de `ReadOnlyFile` para o arquivo TextFile1.txt.  O código usa associação tardia para chamar membros dinâmicos e recuperar linhas de texto que contêm a cadeia de caracteres “” cliente.  
  
     [!code-cs[VbDynamicWalkthrough#8](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_8.cs)]
     [!code-vb[VbDynamicWalkthrough#8](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_8.vb)]  
  
3.  Salve o arquivo e pressione CTRL \+ f5 para compilar e executar o aplicativo.  
  
## Chamando uma biblioteca dinâmica de linguagem  
 O projeto seguir que você cria em acessos de este passo\-a\-passo uma biblioteca que foi escrito na linguagem IronPython dinâmico.  Antes de criar o projeto, você deve ter IronPython 2.6.1 para .NET 4,0 instalado.  você pode baixar IronPython 2.6.1 para .NET 4,0 de [CodePlex](http://go.microsoft.com/fwlink/?LinkId=187223).  
  
#### Para criar uma classe dinâmica personalizado  
  
1.  Em [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], no menu **File**, aponte para **New** e então clique em **Project**.  
  
2.  Em a caixa de diálogo de **Novo Projeto** , no painel de **Tipos de projeto** , certifique\-se que está selecionado **Janelas** .  **Aplicativo de Console** Selecione no painel de **Modelos** .  Em a caixa de **Nome** , o tipo `DynamicIronPythonSample`, e clique em **OK**.  o novo projeto é criado.  
  
3.  Se você estiver usando [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], clique com o botão direito do mouse no projeto de DynamicIronPythonSample e clique em **Propriedades**.  Clique na aba **References**.  Clique no botão **Add**.  Se você estiver usando o visual C\#, em **Gerenciador de Soluções**, clique com o botão direito do mouse na pasta de **Referências** e clique em **Adicionar Referência**.  
  
4.  Em a guia de **Procurar** , navegue até a pasta onde as bibliotecas de IronPython são instaladas.  Por exemplo, C:\\Program Files\\IronPython .NET 2,6 para 4,0.  Selecione **IronPython.dll**, **IronPython.Modules.dll**, **Microsoft.Scripting.dll**, e bibliotecas de **Microsoft.Dynamic.dll** .  Clique em **OK**.  
  
5.  Se você estiver usando [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], edite o arquivo Module1.vb.  Se você estiver usando o visual C\#, edite o arquivo de Module.vb.  
  
6.  Em a parte superior do arquivo, adicione o seguinte código para importar `Microsoft.Scripting.Hosting` e namespaces de `IronPython.Hosting` as bibliotecas de IronPython.  
  
     [!code-cs[VbDynamicWalkthroughIronPython#1](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_9.cs)]
     [!code-vb[VbDynamicWalkthroughIronPython#1](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_9.vb)]  
  
7.  Em o método principal, adicione o seguinte código para criar um novo objeto de `Microsoft.Scripting.Hosting.ScriptRuntime` para hospedar as bibliotecas de IronPython.  O objeto de `ScriptRuntime` carrega o módulo random.py de biblioteca de IronPython.  
  
     [!code-cs[VbDynamicWalkthroughIronPython#2](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_10.cs)]
     [!code-vb[VbDynamicWalkthroughIronPython#2](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_10.vb)]  
  
8.  Depois que o código para carregar o módulo de random.py, adicione o seguinte código para criar uma matriz de inteiros.  A matriz é passada para o método de `shuffle` módulo de random.py, que classes aleatoriamente os valores na matriz.  
  
     [!code-cs[VbDynamicWalkthroughIronPython#3](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_11.cs)]
     [!code-vb[VbDynamicWalkthroughIronPython#3](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_11.vb)]  
  
9. Salve o arquivo e pressione CTRL \+ f5 para compilar e executar o aplicativo.  
  
## Consulte também  
 <xref:System.Dynamic?displayProperty=fullName>   
 <xref:System.Dynamic.DynamicObject?displayProperty=fullName>   
 [Usando o tipo dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [Associação antecipada e tardia](../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md)   
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)   
 [Implementando interfaces dinâmicos \(blog externa\)](http://go.microsoft.com/fwlink/?LinkId=230895)