---
title: "Passo a passo: Programação do Office (C# e Visual Basic) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- Office, programming in Visual Basic and C#
- Office programming [C#]
- Office programming [Visual Basic]
ms.assetid: 519cff31-f80b-4f0e-a56b-26358d0f8c51
caps.latest.revision: 46
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
ms.openlocfilehash: f93a5403660ca850d6650a1a6406395dfa2cc2e5
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-office-programming-c-and-visual-basic"></a>Passo a passo: Programação do Office (C# e Visual Basic)
[!INCLUDE[vs_dev10_long](../../../csharp/programming-guide/interop/includes/vs_dev10_long_md.md)] apresenta novos recursos no C# e no Visual Basic que melhoram a programação do Microsoft Office. Cada linguagem adicionou recursos que já existiam na outra linguagem.  
  
 Os novos recursos em C# incluem argumentos nomeados e opcionais, retornam valores que possuem o tipo `dynamic` e, em programação COM, a capacidade de omitir a palavra-chave `ref` e acessar propriedades indexadas. Os novos recursos do Visual Basic incluem propriedades implementadas automaticamente, instruções em expressões lambda e inicializadores de coleção.  
  
 Ambas as linguagens permitem incorporar as informações de tipo, que permitem a implantação de assemblies que interagem com componentes COM sem implantar assemblies de interoperabilidade primários (PIAs) no computador do usuário. Para obter mais informações, consulte [Instruções passo a passo: Inserindo tipos de assemblies gerenciados](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).  
  
 Este passo a passo demonstra os novos recursos no contexto de programação do Office, mas muitos deles também são úteis na programação em geral. No passo a passo, você primeiro usará um aplicativo Suplemento do Excel para criar uma planilha do Excel. Em seguida, você criará um documento do Word que contém um link para a pasta de trabalho. Por fim, você verá como a dependência de PIA pode ser ativada e desativada.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você deve ter o Microsoft Office Excel 2013 (ou versão 2007 ou posterior) e o Microsoft Office Word 2013 (ou versão 2007 ou posterior) instalado no computador para concluir este passo a passo.  
  
 Se você estiver usando um sistema operacional anterior ao [!INCLUDE[windowsver](../../../csharp/programming-guide/interop/includes/windowsver_md.md)], certifique-se de que [!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong_md.md)] esteja instalado.  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-set-up-an-excel-add-in-application"></a>Para configurar um aplicativo Suplemento do Excel  
  
1.  Inicie o Visual Studio.  
  
2.  No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
3.  No painel **Modelos Instalados**, expanda **Visual Basic** ou **Visual C#**, expanda **Office** e, em seguida, clique em **2013** (ou **2010** ou **2007**).  
  
4.  No painel **Modelos**, clique em **Suplemento do Excel 2013** (ou **Suplemento do Excel 2010** ou **Suplemento do Excel 2007**).  
  
5.  Observe a parte superior do painel **Modelos** para se certificar de que **.NET Framework 4** ou uma versão posterior, é exibido na caixa **Estrutura de Destino**.  
  
6.  Digite um nome para seu projeto na caixa **Nome**, se desejar.  
  
7.  Clique em **OK**.  
  
8.  O novo projeto aparece no **Gerenciador de Soluções**.  
  
### <a name="to-add-references"></a>Para adicionar referências  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no nome do projeto e, em seguida, clique em **Adicionar Referência**. A caixa de diálogo **Adicionar Referência** é exibida.  
  
2.  Na guia **Assemblies**, selecione **Microsoft.Office.Interop.Excel**, versão 15.0.0.0 (ou versão 14.0.0.0 para Excel 2010 ou versão 12.0.0.0 para Excel 2007), na lista **Nome do Componente** e, em seguida, mantenha pressionada a tecla CTRL e selecione **Microsoft.Office.Interop.Word**, versão 15.0.0.0 (ou versão 14.0.0.0 para Word 2010 ou 12.0.0.0 para Word 2007).  Se você não vir os assemblies, talvez seja necessário verificar se eles estão instalados e exibidos (consulte [Como: Instalar assemblies de interoperabilidade primária do Office](http://msdn.microsoft.com/library/92948fcc-76c6-4b08-ba63-cab59dd60eb1)).  
  
3.  Clique em **OK**.  
  
### <a name="to-add-necessary-imports-statements-or-using-directives"></a>Para adicionar instruções Imports necessárias ou diretivas de uso  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo **ThisAddIn.vb** ou **ThisAddIn.cs** e clique em **Exibir Código**.  
  
2.  Adicione as seguintes instruções `Imports` (Visual Basic) ou diretivas `using` (C#) à parte superior do arquivo de código, se elas ainda não estiverem presentes.  
  
     [!code-cs[csOfficeWalkthrough#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_1.cs)]
     [!code-vb[csOfficeWalkthrough#1](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_1.vb)]  
  
### <a name="to-create-a-list-of-bank-accounts"></a>Para criar uma lista de contas bancárias  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no nome do projeto, clique em **Adicionar** e clique em **Classe**. Nomeie a classe Account.vb se você estiver usando Visual Basic ou Account.cs, se você estiver usando C#. Clique em **Adicionar**.  
  
2.  Substitua a definição da classe `Account` pelo código a seguir. As definições de classe usam *propriedades autoimplementadas*, novas no Visual Basic no Visual Studio 2010. Para obter mais informações, consulte [Propriedades autoimplementadas](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).  
  
     [!code-cs[csOfficeWalkthrough#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_2.cs)]
     [!code-vb[csOfficeWalkthrough#2](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_2.vb)]  
  
3.  Para criar uma lista `bankAccounts` que contém duas contas, adicione o seguinte código ao método `ThisAddIn_Startup` em ThisAddIn.vb ou ThisAddIn.cs. As declarações da lista usam *inicializadores de coleção*, novos no Visual Basic no Visual Studio 2010. Para obter mais informações, consulte [Inicializadores de coleção](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).  
  
     [!code-cs[csOfficeWalkthrough#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_3.cs)]
     [!code-vb[csOfficeWalkthrough#3](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_3.vb)]  
  
### <a name="to-export-data-to-excel"></a>Para exportar dados para o Excel  
  
1.  No mesmo arquivo, adicione o método a seguir para a classe `ThisAddIn`. O método configura uma planilha do Excel e exporta dados para ela.  
  
     [!code-cs[csOfficeWalkthrough#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_4.cs)]
     [!code-vb[csOfficeWalkthrough#4](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_4.vb)]  
  
     Dois novos recursos do C# são usados neste método. Esses dois recursos já existem no Visual Basic.  
  
    -   O método [Add](http://go.microsoft.com/fwlink/?LinkId=210910) tem um *parâmetro opcional* para especificar um modelo específico. Parâmetros opcionais, novos no [!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp_dev10_long_md.md)], permitem omitir o argumento para esse parâmetro, se você deseja usar o valor padrão do parâmetro. Como nenhum argumento é enviado no código anterior, `Add` usa o modelo padrão e cria uma nova pasta de trabalho. A instrução equivalente em versões anteriores do C# requer um argumento de espaço reservado: `excelApp.Workbooks.Add(Type.Missing)`.  
  
         Para obter mais informações, consulte [Argumentos nomeados e opcionais](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md).  
  
    -   As propriedades `Range` e `Offset` do objeto [Range](http://go.microsoft.com/fwlink/?LinkId=210911) usam o recurso de *propriedades indexadas*. Este recurso permite consumir essas propriedades de tipos COM usando a sintaxe típica do C# a seguir. Propriedades indexadas também permitem que você use a propriedade `Value` do objeto `Range`, eliminando a necessidade de usar a propriedade `Value2`. A propriedade `Value` é indexada, mas o índice é opcional. Argumentos opcionais e propriedades indexadas trabalham juntos no exemplo a seguir.  
  
         [!code-cs[csOfficeWalkthrough#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_5.cs)]  
  
         Em versões anteriores da linguagem, a sintaxe especial a seguir é obrigatória.  
  
         [!code-cs[csOfficeWalkthrough#6](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_6.cs)]  
  
         Não é possível criar propriedades indexadas de sua preferência. O recurso dá suporte apenas ao consumo de propriedades indexadas existentes.  
  
         Para obter mais informações, consulte [Como usar propriedades indexadas na programação para interoperabilidade COM](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md).  
  
2.  Adicione o seguinte código no final de `DisplayInExcel` para ajustar as larguras das colunas para adequar o conteúdo.  
  
     [!code-cs[csOfficeWalkthrough#7](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_7.cs)]
     [!code-vb[csOfficeWalkthrough#7](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_7.vb)]  
  
     Essas adições demonstram outro recurso novo em C# 2010: tratar valores `Object` retornados de hosts COM como o Office, como se eles tivessem o tipo [dinâmico](../../../csharp/language-reference/keywords/dynamic.md). Isso acontece automaticamente quando **Inserir Tipos de Interoperabilidade** está definido como o valor padrão, `True` ou, de forma equivalente, quando o assembly é referenciado pela opção do compilador [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md). O tipo `dynamic` permite a vinculação posterior, já disponível no Visual Basic, e evita a conversão explícita necessária no Visual C# 2008 e em versões anteriores da linguagem.  
  
     Por exemplo, `excelApp.Columns[1]` retorna um `Object` e `AutoFit` é um método [Range](http://go.microsoft.com/fwlink/?LinkId=210911) do Excel. Sem `dynamic`, você deve converter o objeto retornado em `excelApp.Columns[1]` como uma instância de `Range` antes de chamar o método `AutoFit`.  
  
     [!code-cs[csOfficeWalkthrough#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_8.cs)]  
  
     Para obter mais informações sobre como inserir tipos de interoperabilidade, consulte os procedimentos "Para localizar a referência de PIA" e "Para restaurar a dependência de PIA" posteriormente neste tópico. Para obter mais informações sobre `dynamic`, consulte [dynamic](../../../csharp/language-reference/keywords/dynamic.md) ou [Usando o tipo dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).  
  
### <a name="to-invoke-displayinexcel"></a>Para invocar DisplayInExcel  
  
1.  Adicione o código a seguir no final do método `ThisAddIn_StartUp`. A chamada para `DisplayInExcel` contém dois argumentos. O primeiro argumento é o nome da lista de contas a ser processada. O segundo argumento é uma expressão lambda com várias linhas que define como os dados deverão ser processados. Os valores `ID` e `balance` de cada conta serão exibidos em células adjacentes e a linha será exibida em vermelho se o equilíbrio for menor do que zero. Expressões lambda com várias linhas são um novo recurso do Visual Basic 2010. Para obter mais informações, consulte [Expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
     [!code-cs[csOfficeWalkthrough#9](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_9.cs)]
     [!code-vb[csOfficeWalkthrough#9](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_9.vb)]  
  
2.  Para executar o programa, pressione F5. Uma planilha do Excel é exibida contendo os dados das contas.  
  
### <a name="to-add-a-word-document"></a>Para adicionar um documento do Word  
  
1.  Adicione o código a seguir ao final do método `ThisAddIn_StartUp` para criar um documento do Word que contém um link para a pasta de trabalho do Excel.  
  
     [!code-cs[csOfficeWalkthrough#10](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_10.cs)]
     [!code-vb[csOfficeWalkthrough#10](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_10.vb)]  
  
     Esse código demonstra vários dos novos recursos no C#: a capacidade para omitir a palavra-chave `ref` em programação COM, argumentos nomeados e argumentos opcionais. Esses recursos já existem no Visual Basic. O método [PasteSpecial](http://go.microsoft.com/fwlink/?LinkId=147099) tem sete parâmetros, que são definidos como parâmetros de referência opcionais. Antes do Visual C# 2010, era necessário definir as variáveis de objeto a serem usadas como argumentos para os sete parâmetros, mesmo quando você não tinha nenhum valor significativo para enviar. Argumentos opcionais e nomeados permitem designar os parâmetros que você deseja acessar pelo nome e enviar argumentos apenas para esses parâmetros. Neste exemplo, os argumentos são enviados para indicar que deve ser criado um link para a pasta de trabalho na área de transferência (parâmetro `Link`), e que o link será exibido no documento do Word como um ícone (parâmetro `DisplayAsIcon`). O Visual c# 2010 permite também que você omita a palavra-chave `ref` nesses argumentos. Compare o segmento de código a seguir do Visual C# 2008 com a única linha necessária no Visual C# 2010:  
  
     [!code-cs[csOfficeWalkthrough#11](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_11.cs)]  
  
### <a name="to-run-the-application"></a>Para executar o aplicativo  
  
1.  Pressione F5 para executar o aplicativo. O Excel é iniciado e exibe uma tabela que contém as informações das duas contas em `bankAccounts`. Em seguida, um documento do Word é exibido contendo um link para a tabela do Excel.  
  
### <a name="to-clean-up-the-completed-project"></a>Para limpar o projeto concluído  
  
1.  No Visual Studio, clique em **Limpar Solução** no menu **Compilar**. Caso contrário, o suplemento será executado toda vez que você abrir o Excel no seu computador.  
  
### <a name="to-find-the-pia-reference"></a>Para localizar a referência de PIA  
  
1.  Execute o aplicativo novamente, mas não clique em **Limpar Solução**.  
  
2.  No menu **Iniciar**, clique em **Todos os Programas**. Em seguida, clique em **Microsoft Visual Studio 2013**, em **Ferramentas do Visual Studio** e em **Prompt de Comando do Visual Studio (2013)**.  
  
3.  Digite `ildasm` na janela Prompt de Comando do Visual Studio (2013) e pressione ENTER. A janela IL DASM é exibida.  
  
4.  No menu **Arquivo** na janela IL DASM, clique em **Abrir**. Clique duas vezes em **Visual Studio 2013** e clique duas vezes em **Projetos**. Abra a pasta do seu projeto e procure na pasta bin/Debug por *nome do projeto*.dll. Clique duas vezes em *nome do projeto*.dll. Uma nova janela exibe os atributos do projeto, além das referências a outros módulos e assemblies. Observe que os namespaces `Microsoft.Office.Interop.Excel` e `Microsoft.Office.Interop.Word` estão incluídos no assembly. Por padrão, no Visual Studio 2013, o compilador importa os tipos que você precisa de um PIA referenciado para o seu assembly.  
  
     Para obter mais informações, consulte [Como exibir o conteúdo de um assembly](http://msdn.microsoft.com/library/fb7baaab-4c0d-47ad-8fd3-4591cf834709).  
  
5.  Clique duas vezes no ícone **MANIFEST**. Uma janela será exibida contendo uma lista de assemblies que contêm itens referenciados pelo projeto. `Microsoft.Office.Interop.Excel` e `Microsoft.Office.Interop.Word` não estão incluídos na lista. Como os tipos do seu projeto precisam ter sido importados para o assembly, referências a um PIA não são necessárias. Isso facilita a implantação. Os PIAs não precisam estar presentes no computador do usuário e como um aplicativo não requer a implantação de uma versão específica de um PIA, os aplicativos podem ser projetados para trabalhar com várias versões do Office, desde que as APIs necessárias existam em todas as versões.  
  
     Como a implantação de PIAs não é mais necessária, você pode criar um aplicativo em cenários avançados que funcione com várias versões do Office, incluindo versões anteriores. No entanto, isso funcionará apenas se seu código não usar quaisquer APIs que não estejam disponíveis na versão do Office na qual você está trabalhando. Não é sempre claro se uma determinada API estava disponível em uma versão anterior e, por essa razão, não é recomendado trabalhar com versões anteriores do Office.  
  
    > [!NOTE]
    >  O Office não publicou PIAs antes do Office 2003. Portanto, a única maneira de gerar um assembly de interoperabilidade para o Office 2002 ou versões anteriores é importando referência COM.  
  
6.  Feche a janela do manifesto e a janela do assembly.  
  
### <a name="to-restore-the-pia-dependency"></a>Para restaurar a dependência de PIA  
  
1.  Em **Gerenciador de Soluções**, clique no botão **Mostrar Todos os Arquivos**. Expanda a pasta **Referências** e selecione **Microsoft.Office.Interop.Excel**. Pressione F4 para exibir a janela **Propriedades**.  
  
2.  Na janela **Propriedades**, altere a propriedade **Inserir Tipos de Interoperabilidade** de **True** para **False**.  
  
3.  Repita as etapas 1 e 2 deste procedimento para `Microsoft.Office.Interop.Word`.  
  
4.  Em C#, comente as duas chamadas para `Autofit` no final do método `DisplayInExcel`.  
  
5.  Pressione F5 para verificar se o projeto ainda é executado corretamente.  
  
6.  Repita as etapas de 1 a 3 do procedimento anterior para abrir a janela do assembly. Observe que `Microsoft.Office.Interop.Word` e `Microsoft.Office.Interop.Excel` não estão mais na lista de assemblies inseridos.  
  
7.  Clique duas vezes no ícone **MANIFEST** e role a lista de assemblies referenciados. Ambos `Microsoft.Office.Interop.Word` e `Microsoft.Office.Interop.Excel` estão na lista. Como o aplicativo faz referência aos PIAs do Excel e do Word e a propriedade **Inserir Tipos de Interoperabilidade** está definida como **False**, ambos os assemblies devem existir no computador do usuário final.  
  
8.  No Visual Studio, clique em **Limpar Solução** no menu **Compilar** para limpar o projeto concluído.  
  
## <a name="see-also"></a>Consulte também  
 [Propriedades autoimplementadas](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)   
 [Propriedades autoimplementadas](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)   
 [Inicializadores de Coleção](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)   
 [Inicializadores de Objeto e Coleção](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)   
 [Parâmetros opcionais](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Passando argumentos por posição e nome](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Argumentos nomeados e opcionais](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)   
 [Associação antecipada e tardia](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)   
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)   
 [Usando o Tipo dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [Expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Expressões Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
 [Como usar propriedades indexadas na programação para interoperabilidade COM](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)   
 [Instruções passo a passo: Inserindo informações de tipo dos Microsoft Office Assemblies](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3)   
 [Instruções passo a passo: Inserindo tipos de assemblies gerenciados](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)   
 [Passo a passo: criando o primeiro suplemento do VSTO para Excel](http://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f)   
 [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Interoperabilidade](../../../csharp/programming-guide/interop/index.md)
