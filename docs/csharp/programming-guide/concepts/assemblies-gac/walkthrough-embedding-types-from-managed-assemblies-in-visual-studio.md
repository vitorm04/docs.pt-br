---
title: "Instruções passo a passo: Inserindo tipos de assemblies gerenciados no Visual Studio (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c821afbbe8571d9573321b9d11b069aa0f7cd342
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-c"></a>Passo a passo: inserindo tipos de assemblies gerenciados no Visual Studio (C#)
Se você inserir informações de um assembly gerenciado de nome forte, você poderá acoplar vagamente tipos em um aplicativo para atingir a independência de versão. Isto é, seu programa pode ser escrito para usar tipos de várias versões de uma biblioteca gerenciada sem precisar ser recompilado para cada versão.  
  
 A incorporação de tipo é frequentemente usada com a interoperabilidade COM, como um aplicativo que usa objetos de automação do Microsoft Office. Inserir informações de tipo permite que o mesmo build de um programa funcione com diferentes versões do Microsoft Office em diferentes computadores. No entanto, você também pode usar a inserção de tipo com uma solução totalmente gerenciada.  
  
 As informações de tipo podem ser inseridas de um assembly que tem as seguintes características:  
  
-   O assembly expõe pelo menos uma interface pública.  
  
-   As interfaces inseridas são anotadas com um atributo `ComImport` e um atributo `Guid` (e um GUID único).  
  
-   O assembly é anotado com o atributo `ImportedFromTypeLib` ou o atributo `PrimaryInteropAssembly` e um atributo `Guid` de nível do assembly. (Por padrão, os modelos de projeto do Visual C# incluem um atributo `Guid` de nível do assembly.)  
  
 Depois de especificar as interfaces públicas que podem ser inseridas, você pode criar classes de tempo de execução que implementam essas interfaces. Um programa cliente pode, então, inserir as informações de tipo para essas interfaces em tempo de design referenciando o assembly que contém as interfaces públicas e configurando a propriedade `Embed Interop Types` da referência como `True`. Isso é equivalente a usar o compilador de linha de comando e fazer referência ao assembly usando a opção do compilador `/link`. O programa cliente pode, então, carregar instâncias de seus objetos de tempo de execução de tipo como essas interfaces. Se você criar uma nova versão do seu assembly de tempo de execução de nome forte, o programa cliente não precisará ser recompilado com o assembly de tempo de execução atualizado. Em vez disso, o programa cliente continua a usar qualquer versão do assembly em tempo de execução que está disponível para ele, usando as informações de tipo inseridas para as interfaces públicas.  
  
 Como a principal função da inserção de tipo é dar suporte à inserção de informações de tipo dos assemblies de interoperabilidade COM, as limitações a seguir se aplicam ao inserir informações em uma solução totalmente gerenciada:  
  
-   Somente os atributos específicos à interoperabilidade COM são inseridos, outros atributos são ignorados.  
  
-   Se um tipo usar parâmetros genéricos e o tipo de parâmetro genérico for um tipo inserido, esse tipo não poderá ser usado em um limite de assembly. Os exemplos de cruzar um limite de assembly incluem chamar um método de outro assembly ou derivar um tipo de um tipo definido em outro assembly.  
  
-   Constantes não são inseridas.  
  
-   A classe <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> não dá suporte a um tipo inserido como uma chave. Você pode implementar seu próprio tipo de dicionário para dar suporte a um tipo inserido como uma chave.  
  
 Neste passo a passo, você fará o seguinte:  
  
-   Criará um assembly de nome forte que tem uma interface pública que contém informações de tipo que podem ser inseridas.  
  
-   Criará um assembly de tempo de execução de nome forte que implementa a interface pública.  
  
-   Criará um programa cliente que insere as informações de tipo da interface pública e criará uma instância da classe do assembly de tempo de execução.  
  
-   Modificará e recompilará o assembly de tempo de execução.  
  
-   Executará o programa cliente para ver se a nova versão do assembly de tempo de execução está sendo usado sem a necessidade de recompilar o programa cliente.  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="creating-an-interface"></a>Criando uma interface  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a>Para criar o projeto de interface de equivalência de tipo  
  
1.  No Visual Studio, no menu **Arquivo**, escolha **Novo** e clique em **Projeto**.  
  
2.  Na caixa de diálogo **Novo Projeto**, no painel **Tipos de Projetos**, certifique-se de que **Windows** esteja selecionado. Selecione **Biblioteca de Classes** no painel **Modelos**. Na caixa **Nome**, digite `TypeEquivalenceInterface` e clique em **OK**. O novo projeto é criado.  
  
3.  Em **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo Class1.cs e clique em **Renomear**. Renomeie o arquivo como `ISampleInterface.cs` e pressione ENTER. Renomear o arquivo também renomeará a classe para `ISampleInterface`. Essa classe representará a interface pública para a classe.  
  
4.  Clique com o botão direito do mouse no projeto TypeEquivalenceInterface e clique em **Propriedades**. Clique na guia **Build**. Defina o caminho de saída para um local válido no computador de desenvolvimento, como `C:\TypeEquivalenceSample`. Esse local também será usado em uma etapa posterior neste passo a passo.  
  
5.  Enquanto ainda estiver editando as propriedades do projeto, clique na guia **Assinatura**. Selecione a opção **Assinar o assembly**. Na lista **Escolha um arquivo de chave de nome forte**, clique em **<Novo...>**. Na caixa **Nome de arquivo de chave**, digite `key.snk`. Desmarque a caixa de seleção **Proteger o arquivo de chaves com senha**. Clique em **OK**.  
  
6.  Abra o arquivo ISampleInterface.cs. Adicione o seguinte código ao arquivo de classe ISampleInterface para criar a interface ISampleInterface.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
7.  No menu **Ferramentas**, clique em **Criar GUID**. Na caixa de diálogo **Criar GUID**, clique em **Formato do Registro** e clique em **Copiar**. Clique em **Sair**.  
  
8.  No atributo `Guid`, exclua o GUID de exemplo e cole o GUID que você copiou da caixa de diálogo **Criar GUID**. Remova as chaves ({}) do GUID copiado.  
  
9. No **Gerenciador de Soluções**, expanda a pasta **Propriedades**. Clique duas vezes no arquivo AssemblyInfo.cs. Adicione o seguinte atributo ao arquivo.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
     Salve o arquivo.  
  
10. Salvar o projeto.  
  
11. Clique com o botão direito do mouse no projeto TypeEquivalenceInterface e clique em **Build**. O arquivo .dll da biblioteca de classes é compilado e salvo no caminho de saída de build especificado (por exemplo, C:\TypeEquivalenceSample).  
  
## <a name="creating-a-runtime-class"></a>Criando uma classe de tempo de execução  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a>Para criar o projeto de tempo de execução de equivalência de tipo  
  
1.  No Visual Studio, no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
2.  Na caixa de diálogo **Novo Projeto**, no painel **Tipos de Projetos**, certifique-se de que **Windows** esteja selecionado. Selecione **Biblioteca de Classes** no painel **Modelos**. Na caixa **Nome**, digite `TypeEquivalenceRuntime` e clique em **OK**. O novo projeto é criado.  
  
3.  Em **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo Class1.cs e clique em **Renomear**. Renomeie o arquivo como `SampleClass.cs` e pressione ENTER. Renomear o arquivo também renomeia a classe para `SampleClass`. Essa classe implementará a interface `ISampleInterface`.  
  
4.  Clique com o botão direito do mouse no projeto TypeEquivalenceRuntime e clique em **Propriedades**. Clique na guia **Build**. Defina o caminho de saída para o mesmo local usado no projeto TypeEquivalenceInterface, por exemplo, `C:\TypeEquivalenceSample`.  
  
5.  Enquanto ainda estiver editando as propriedades do projeto, clique na guia **Assinatura**. Selecione a opção **Assinar o assembly**. Na lista **Escolha um arquivo de chave de nome forte**, clique em **<Novo...>**. Na caixa **Nome de arquivo de chave**, digite `key.snk`. Desmarque a caixa de seleção **Proteger o arquivo de chaves com senha**. Clique em **OK**.  
  
6.  Clique com o botão direito do mouse no projeto TypeEquivalenceRuntime e clique em **Adicionar Referência**. Clique na guia **Procurar** e navegue até a pasta do caminho de saída. Selecione o arquivo TypeEquivalenceInterface.dll e clique em **OK**.  
  
7.  No **Gerenciador de Soluções**, expanda a pasta **Referências**. Selecione a referência TypeEquivalenceInterface. Na janela Propriedades para a referência de TypeEquivalenceInterface, defina a propriedade **Versão Específica** como **False**.  
  
8.  Adicione o código a seguir ao arquivo de classe SampleClass para criar a classe SampleClass.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
9. Salvar o projeto.  
  
10. Clique com o botão direito do mouse no projeto TypeEquivalenceRuntime e clique em **Compilar**. O arquivo .dll da biblioteca de classes é compilado e salvo no caminho de saída de build especificado (por exemplo, C:\TypeEquivalenceSample).  
  
## <a name="creating-a-client-project"></a>Criando um projeto de cliente  
  
#### <a name="to-create-the-type-equivalence-client-project"></a>Para criar o projeto de cliente de equivalência de tipo  
  
1.  No Visual Studio, no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
2.  Na caixa de diálogo **Novo Projeto**, no painel **Tipos de Projetos**, certifique-se de que **Windows** esteja selecionado. Selecione **Aplicativo de Console** no painel **Modelos**. Na caixa **Nome**, digite `TypeEquivalenceClient` e clique em **OK**. O novo projeto é criado.  
  
3.  Clique com o botão direito do mouse no projeto TypeEquivalenceClient e clique em **Propriedades**. Clique na guia **Build**. Defina o caminho de saída para o mesmo local usado no projeto TypeEquivalenceInterface, por exemplo, `C:\TypeEquivalenceSample`.  
  
4.  Clique com o botão direito do mouse no projeto TypeEquivalenceClient e clique em **Adicionar Referência**. Clique na guia **Procurar** e navegue até a pasta do caminho de saída. Selecione o arquivo TypeEquivalenceInterface.dll (não o TypeEquivalenceRuntime.dll) e clique em **OK**.  
  
5.  No **Gerenciador de Soluções**, expanda a pasta **Referências**. Selecione a referência TypeEquivalenceInterface. Na janela Propriedades para a referência de TypeEquivalenceInterface, defina a propriedade **Inserir Tipos de Interoperabilidade** como **True**.  
  
6.  Adicione o seguinte código ao arquivo Program.cs para criar o programa cliente.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
7.  Pressione CTRL+F5 para compilar e executar o programa.  
  
## <a name="modifying-the-interface"></a>Modificando a interface  
  
#### <a name="to-modify-the-interface"></a>Para modificar a interface  
  
1.  No Visual Studio, no menu **Arquivo**, aponte para **Abrir** e clique em **Projeto/Solução**.  
  
2.  Na caixa de diálogo **Abrir Projeto**, clique com o botão direito do mouse no projeto TypeEquivalenceInterface e clique em **Propriedades**. Clique na guia **Aplicativo**. Clique no botão **Informações do Assembly**. Altere os valores de **Versão do Assembly** e **Versão do Arquivo** para `2.0.0.0`.  
  
3.  Abra o arquivo SampleInterface.cs. Adicione a linha de código a seguir à interface ISampleInterface.  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
     Salve o arquivo.  
  
4.  Salvar o projeto.  
  
5.  Clique com o botão direito do mouse no projeto TypeEquivalenceInterface e clique em **Build**. Uma nova versão do arquivo .dll da biblioteca de classes é compilada e salva no caminho de saída de build especificado (por exemplo, C:\TypeEquivalenceSample).  
  
## <a name="modifying-the-runtime-class"></a>Modificar a classe de tempo de execução  
  
#### <a name="to-modify-the-runtime-class"></a>Para modificar a classe de tempo de execução  
  
1.  No Visual Studio, no menu **Arquivo**, aponte para **Abrir** e clique em **Projeto/Solução**.  
  
2.  Na caixa de diálogo **Abrir Projeto**, clique com o botão direito do mouse no projeto TypeEquivalenceRuntime e clique em **Propriedades**. Clique na guia **Aplicativo**. Clique no botão **Informações do Assembly**. Altere os valores de **Versão do Assembly** e **Versão do Arquivo** para `2.0.0.0`.  
  
3.  Abra o arquivo SampleClass.cs. Adicione as seguintes linhas de código à classe SampleClass.  
  
    ```cs  
    public DateTime GetDate()  
    {  
        return DateTime.Now;  
    }  
    ```  
  
     Salve o arquivo.  
  
4.  Salvar o projeto.  
  
5.  Clique com o botão direito do mouse no projeto TypeEquivalenceRuntime e clique em **Compilar**. Uma versão atualizada do arquivo .dll da biblioteca de classes é compilada e salva no caminho de saída de build especificado anteriormente (por exemplo, C:\TypeEquivalenceSample).  
  
6.  No Explorador de Arquivos, abra a pasta do caminho de saída (por exemplo, C:\TypeEquivalenceSample). Clique duas vezes em TypeEquivalenceClient.exe para executar o programa. O programa refletirá a nova versão do assembly TypeEquivalenceRuntime sem ter sido recompilado.  
  
## <a name="see-also"></a>Consulte também  
 [/link (opções do compilador C#)](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)   
 [Guia de Programação em C#](../../../../csharp/programming-guide/index.md)   
 [Programação com assemblies](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6)   
 [Assemblies e o Cache de Assembly Global (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)

