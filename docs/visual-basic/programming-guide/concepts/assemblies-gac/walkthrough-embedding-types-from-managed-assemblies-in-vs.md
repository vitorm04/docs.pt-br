---
title: 'Passo a passo: Inserindo tipos de Assemblies no Visual Studio (Visual Basic) gerenciado | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 56ed12ba-adff-4e9c-a668-7fcba80c4795
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: adc58e081cd9b874a841d84b11d92cbffb6ba6b8
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-visual-basic"></a>Passo a passo: Inserindo tipos de Assemblies gerenciados no Visual Studio (Visual Basic)
Se você inserir informações de um assembly gerenciado com nome forte, você pode acoplar vagamente tipos em um aplicativo para atingir a independência de versão. Isto é, seu programa pode ser escrito para usar tipos de várias versões de uma biblioteca gerenciada sem precisar ser recompilado para cada versão.  
  
 Incorporação de tipo é frequentemente usado com interoperabilidade de COM, como um aplicativo que usa objetos de automação do Microsoft Office. Inserindo informações de tipo permite que a mesma compilação de um programa para trabalhar com diferentes versões do Microsoft Office em computadores diferentes. No entanto, você também pode usar o tipo de inserção com uma solução totalmente gerenciada.  
  
 Informações de tipo podem ser inseridas de um assembly que tem as seguintes características:  
  
-   O assembly expõe pelo menos uma interface pública.  
  
-   As interfaces incorporadas são anotadas com um `ComImport` atributo e um `Guid` atributo (e um GUID exclusivo).  
  
-   O assembly é anotado com a `ImportedFromTypeLib` atributo ou o `PrimaryInteropAssembly` atributo e um nível de conjunto `Guid` atributo. (Por padrão, os modelos de projeto do Visual Basic incluem um nível de conjunto `Guid` atributo.)  
  
 Depois de especificar as interfaces públicas que podem ser inseridas, você pode criar classes de tempo de execução que implementam essas interfaces. Um programa cliente pode, em seguida, inserir as informações de tipo para essas interfaces em tempo de design referenciando o assembly que contém a configuração e as interfaces públicas de `Embed Interop Types` a referência à propriedade `True`. Isso é equivalente a usar o compilador de linha de comando e faça referência ao assembly usando o `/link` opção de compilador. O programa cliente pode, em seguida, carregar instâncias de seus objetos de tempo de execução digitados como essas interfaces. Se você criar uma nova versão do seu assembly de nome forte em tempo de execução, o programa cliente não tem que ser recompilados com o assembly de tempo de execução atualizado. Em vez disso, o programa cliente continuará a usar qualquer versão do assembly em tempo de execução está disponível, usando as informações de tipo inserido para as interfaces públicas.  
  
 Como é a principal função de inserção de tipo oferecer suporte a incorporação de informações de tipo de módulos de interoperabilidade COM, as seguintes limitações se aplicam quando você insere informações de tipo em uma solução totalmente gerenciada:  
  
-   Somente os atributos específicos à interoperabilidade COM são incorporados. outros atributos são ignorados.  
  
-   Se um tipo usa parâmetros genéricos e o tipo de parâmetro genérico é um tipo inserido, esse tipo não pode ser usado em um limite de conjunto. Cruzar um limite de conjunto exemplos de chamar um método de outro assembly ou derivar um tipo de um tipo definido em outro assembly.  
  
-   Constantes não são incorporadas.  
  
-   O <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>classe não oferece suporte a um tipo inserido como uma chave.</xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> Você pode implementar seu próprio tipo de dicionário para dar suporte a um tipo inserido como uma chave.  
  
 Neste passo a passo, você irá fazer o seguinte:  
  
-   Crie um assembly de nome forte que tem uma interface pública que contém informações de tipo que podem ser inseridas.  
  
-   Crie um assembly de nome forte em tempo de execução que implementa a interface pública.  
  
-   Crie um programa cliente que incorpora informações de tipo de interface pública e cria uma instância da classe do assembly de tempo de execução.  
  
-   Modificar e recompilar o assembly de tempo de execução.  
  
-   Execute o programa de cliente para ver que a nova versão do assembly em tempo de execução está sendo usada sem ter que recompilar o programa cliente.  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="creating-an-interface"></a>Criando uma Interface  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a>Para criar o projeto de interface de equivalência de tipo  
  
1.  No Visual Studio, no **arquivo** , aponte para **novo** e, em seguida, clique em **projeto**.  
  
2.  No **novo projeto** na caixa de **tipos de projeto** painel, verifique se **Windows** está selecionado. Selecione **biblioteca de classes** no **modelos** painel. No **nome** , digite `TypeEquivalenceInterface`e, em seguida, clique em **Okey**. O novo projeto é criado.  
  
3.  Em **Solution Explorer**, clique no arquivo Class1. vb e clique em **Renomear**. Renomeie o arquivo como `ISampleInterface.vb` e pressione ENTER. Renomear o arquivo também renomear a classe `ISampleInterface`. Essa classe representará a interface pública para a classe.  
  
4.  Clique no projeto TypeEquivalenceInterface **propriedades**. Clique na guia **Compilar**. Definir o caminho de saída para um local válido no computador de desenvolvimento, como `C:\TypeEquivalenceSample`. Esse local também poderá ser usado em uma etapa posterior neste passo a passo.  
  
5.  Enquanto ainda editando as propriedades do projeto, clique o **assinatura** guia. Selecione o **assinar o assembly** opção. No **escolher um arquivo de chave de nome forte** lista, clique em ** <New...> **.</New...> No **nome do arquivo de chave** , digite `key.snk`. Limpar o **proteger meu arquivo de chave com uma senha** caixa de seleção. Clique em **OK**.  
  
6.  Abra o arquivo ISampleInterface.vb. Adicione o seguinte código ao arquivo de classe ISampleInterface para criar a interface ISampleInterface.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
7.  Sobre o **ferramentas** menu, clique em **criar Guid**. No **criar GUID** caixa de diálogo, clique em **formato do registro** e, em seguida, clique em **cópia**. Clique em **Sair**.  
  
8.  No `Guid` de atributo, exclua o GUID de exemplo e cole o GUID que você copiou do **criar GUID** caixa de diálogo. Remova as chaves ({}) do GUID copiado.  
  
9. Sobre o **projeto** menu, clique em **Mostrar todos os arquivos**.  
  
10. Em **Solution Explorer**, expanda o **meu projeto** pasta. Clique duas vezes o AssemblyInfo. Adicione o seguinte atributo ao arquivo.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
     Salve o arquivo.  
  
11. Salvar o projeto.  
  
12. Clique no projeto TypeEquivalenceInterface **criar**. O arquivo. dll da biblioteca de classe é compilado e salvo para o caminho de saída de compilação especificado (por exemplo, C:\TypeEquivalenceSample).  
  
## <a name="creating-a-runtime-class"></a>Criando uma classe de tempo de execução  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a>Para criar o projeto de tempo de execução de equivalência de tipo  
  
1.  No Visual Studio, no **arquivo** , aponte para **novo** e, em seguida, clique em **projeto**.  
  
2.  No **novo projeto** na caixa de **tipos de projeto** painel, verifique se **Windows** está selecionado. Selecione **biblioteca de classes** no **modelos** painel. No **nome** , digite `TypeEquivalenceRuntime`e, em seguida, clique em **Okey**. O novo projeto é criado.  
  
3.  Em **Solution Explorer**, clique no arquivo Class1. vb e clique em **Renomear**. Renomeie o arquivo como `SampleClass.vb` e pressione ENTER. Renomear o arquivo também renomeia a classe `SampleClass`. Essa classe implementará o `ISampleInterface` interface.  
  
4.  Clique no projeto TypeEquivalenceRuntime **propriedades**. Clique na guia **Compilar**. Definir o caminho de saída para o mesmo local usado no projeto TypeEquivalenceInterface, por exemplo, `C:\TypeEquivalenceSample`.  
  
5.  Enquanto ainda editando as propriedades do projeto, clique o **assinatura** guia. Selecione o **assinar o assembly** opção. No **escolher um arquivo de chave de nome forte** lista, clique em ** <New...> **.</New...> No **nome do arquivo de chave** , digite `key.snk`. Limpar o **proteger meu arquivo de chave com uma senha** caixa de seleção. Clique em **OK**.  
  
6.  Clique no projeto TypeEquivalenceRuntime **adicionar referência**. Clique o **procurar** guia e navegue até a pasta do caminho de saída. Selecione o arquivo TypeEquivalenceInterface.dll e clique em **Okey**.  
  
7.  Sobre o **projeto** menu, clique em **Mostrar todos os arquivos**.  
  
8.  Em **Solution Explorer**, expanda o **referências** pasta. Selecione a referência de TypeEquivalenceInterface. Na janela Propriedades para a referência de TypeEquivalenceInterface, defina o **versão específica** propriedade **False**.  
  
9. Adicione o seguinte código ao arquivo de classe SampleClass para criar a classe SampleClass.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
10. Salvar o projeto.  
  
11. Clique no projeto TypeEquivalenceRuntime **criar**. O arquivo. dll da biblioteca de classe é compilado e salvo para o caminho de saída de compilação especificado (por exemplo, C:\TypeEquivalenceSample).  
  
## <a name="creating-a-client-project"></a>Criando um projeto de cliente  
  
#### <a name="to-create-the-type-equivalence-client-project"></a>Para criar o projeto de cliente de equivalência de tipo  
  
1.  No Visual Studio, no **arquivo** , aponte para **novo** e, em seguida, clique em **projeto**.  
  
2.  No **novo projeto** na caixa de **tipos de projeto** painel, verifique se **Windows** está selecionado. Selecione **aplicativo de Console** no **modelos** painel. No **nome** , digite `TypeEquivalenceClient`e, em seguida, clique em **Okey**. O novo projeto é criado.  
  
3.  Clique no projeto TypeEquivalenceClient **propriedades**. Clique na guia **Compilar**. Definir o caminho de saída para o mesmo local usado no projeto TypeEquivalenceInterface, por exemplo, `C:\TypeEquivalenceSample`.  
  
4.  Clique no projeto TypeEquivalenceClient **adicionar referência**. Clique o **procurar** guia e navegue até a pasta do caminho de saída. Selecione o arquivo TypeEquivalenceInterface.dll (não o TypeEquivalenceRuntime.dll) e clique em **Okey**.  
  
5.  Sobre o **projeto** menu, clique em **Mostrar todos os arquivos**.  
  
6.  Em **Solution Explorer**, expanda o **referências** pasta. Selecione a referência de TypeEquivalenceInterface. Na janela Propriedades para a referência de TypeEquivalenceInterface, defina o **inserir tipos Interop** propriedade **True**.  
  
7.  Adicione o seguinte código ao arquivo Module1. vb para criar o programa cliente.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
8.  Pressione CTRL + F5 para compilar e executar o programa.  
  
## <a name="modifying-the-interface"></a>Modificação da Interface  
  
#### <a name="to-modify-the-interface"></a>Para modificar a interface  
  
1.  No Visual Studio, no **arquivo** , aponte para **abrir**e, em seguida, clique em **projeto/solução**.  
  
2.  No **Abrir projeto** caixa de diálogo, clique com botão direito no projeto TypeEquivalenceInterface e, em seguida, clique em **propriedades**. Clique o **aplicativo** guia. Clique o **informações de Assembly** botão. Alterar o **versão do Assembly** e **versão do arquivo** valores `2.0.0.0`.  
  
3.  Abra o arquivo ISampleInterface.vb. Adicione a seguinte linha de código para a interface ISampleInterface.  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
     Salve o arquivo.  
  
4.  Salvar o projeto.  
  
5.  Clique no projeto TypeEquivalenceInterface **criar**. Uma nova versão do arquivo. dll da biblioteca da classe é compilada e salvo no caminho de saída de compilação especificado (por exemplo, C:\TypeEquivalenceSample).  
  
## <a name="modifying-the-runtime-class"></a>Modificar a classe de tempo de execução  
  
#### <a name="to-modify-the-runtime-class"></a>Para modificar a classe de tempo de execução  
  
1.  No Visual Studio, no **arquivo** , aponte para **abrir**e, em seguida, clique em **projeto/solução**.  
  
2.  No **Abrir projeto** caixa de diálogo, clique com botão direito no projeto TypeEquivalenceRuntime e clique em **propriedades**. Clique o **aplicativo** guia. Clique o **informações de Assembly** botão. Alterar o **versão do Assembly** e **versão do arquivo** valores `2.0.0.0`.  
  
3.  Abra o SampleClass.vbfile. Adicione as seguintes linhas de código à classe SampleClass.  
  
```vb  
Public Function GetDate() As DateTime Implements ISampleInterface.GetDate  
    Return Now  
End Function  
```  
  
     Save the file.  
  
4.  Salvar o projeto.  
  
5.  Clique no projeto TypeEquivalenceRuntime **criar**. Uma versão atualizada do arquivo. dll da biblioteca da classe é compilada e salvo no caminho de saída de compilação especificado anteriormente (por exemplo, C:\TypeEquivalenceSample).  
  
6.  No Explorador de arquivos, abra a pasta do caminho de saída (por exemplo, C:\TypeEquivalenceSample). Clique duas vezes em TypeEquivalenceClient.exe para executar o programa. O programa refletirá a nova versão do assembly TypeEquivalenceRuntime sem ter que foi recompilado.  
  
## <a name="see-also"></a>Consulte também  
 [/link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)   
 [Conceitos de programação](../../../../visual-basic/programming-guide/concepts/index.md)   
 [Programação com Assemblies](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6)   
 [Assemblies e o Cache de Assembly Global (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)

