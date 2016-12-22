---
title: "Instru&#231;&#245;es passo a passo: criando objetos COM com o Visual Basic | Microsoft Docs"
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
  - "interoperabilidade COM, Criando objetos COM"
  - "interoperabilidade COM, explicações passo a passo"
  - "objetos COM, criando"
  - "objetos COM, explicações passo a passo"
  - "criação do objeto, objetos COM"
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: criando objetos COM com o Visual Basic
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Ao criar novos aplicativos ou componentes, é melhor criar conjuntos do .NET Framework.  No entanto, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] também facilita a expor um componente do .NET Framework para COM.  Isso permite que você fornecer novos componentes anteriores aplicativo conjuntos que requerem componentes COM.  Essa explicação passo a passo demonstra como usar [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] para expor os objetos [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] como objetos COM, com e sem o modelo classe COM.  
  
 A maneira mais fácil expor objetos COM é usando o modelo classe COM.  O modelo classe COM cria uma nova classe e, em seguida, configura seu projeto para gerar a camada de classe e interoperabilidade como um objeto COM e registrá\-lo com o sistema operacional.  
  
> [!NOTE]
>  Embora você também pode expor uma classe criada em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] como um objeto COM para código não gerenciado para usar, ele não é uma verdadeiro COM objeto e não pode ser usado por [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  Para obter mais informações, consulte [Interoperabilidade COM em aplicativos .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### Para criar um objeto COM, usando o modelo classe COM  
  
1.  Abra um novo projeto aplicativos do Windows a partir do menu **File**,clicando em  **Novo Projeto** .  
  
2.  Na caixa  **Novo Projeto**  caixa de diálogo em  **Tipos de Projeto**  Campo, verifique que o Windows está selecionado.  Selecione  **biblioteca de classes**  a partir de **Templates** Lista e em seguida, clique em  **OK** .  O novo projeto é exibido.  
  
3.  A partir do menu **Project**, selecione **Add New Item**.  A caixa de diálogo **Add New Item** é exibida.  
  
4.  Selecione  **Classe COM** da  **modelos de** e, em seguida, clique  **Add**.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Adiciona uma nova classe e configura o novo projeto para interoperabilidade COM.  
  
5.  Adicione código como propriedades, métodos e eventos para o classe COM.  
  
6.  Selecione  **Build ClassLibrary1** da  **Build** menu.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]cria o assembly e registra o objeto COM o sistema operacional.  
  
## Criando objetos sem o modelo de classe COM  
 Você também pode criar um classe COM instead of manualmente usando o modelo classe COM.  Esse procedimento é útil quando você estiver trabalhando a partir de linha de comando ou quando você deseja ter mais controle sobre Como COM objetos são definidos.  
  
#### Para configurar seu projeto para gerar um objeto COM  
  
1.  Abra um novo projeto de aplicativo do Windows a partir do  **arquivo** menu clicando em  **Newprojeto**.  
  
2.  Na caixa  **Novo Projeto**  caixa de diálogo em  **Tipos de Projeto**  Campo, verifique que o Windows está selecionado.  Selecione  **biblioteca de classes**  a partir de **Templates** Lista e em seguida, clique em  **OK** .  O novo projeto é exibido.  
  
3.  No **Solution Explorer**, clique com o botão direito do mouse no nó do seu projeto e clique em **Properties**.  O  **Project Designer**  é exibida.  
  
4.  Clique na guia **Compile**.  
  
5.  Marque a caixa de seleção **Register for COM interop**.  
  
#### Para configurar o código em sua classe para criar um objeto COM  
  
1.  Em  **Gerenciador de Soluções** ,clique duas vezes em **Class1.vb** para exibir seu código.  
  
2.  Renomeie a classe para `ComClass1`.  
  
3.  Adicione a `ComClass1` constantes a seguir.  Eles armazenará as constantes \(GUID\) que os objetos COM são necessários para ter.  
  
     [!CODE [VbVbalrInterop#2](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrInterop#2)]  
  
4.  Sobre o  **Ferramentas** menu, clique em  **Criar Guid**.  No  **Criar GUID** caixa de diálogo, clique em  **Formato do registro** e, em seguida, clique em  **Copy**.  Clique em  **Exit**.  
  
5.  Substitua a sequência de caracteres vazia para o `ClassId` com o GUID, removendo as chaves à esquerda e à direita.  Por exemplo, se o GUID fornecido pelo Guidgen é `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` Em seguida, seu código deve aparecer da seguinte maneira.  
  
     [!CODE [VbVbalrInterop#3](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrInterop#3)]  
  
6.  Repita as etapas anteriores para o `InterfaceId` e `EventsId` constantes, como no exemplo a seguir.  
  
     [!CODE [VbVbalrInterop#4](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrInterop#4)]  
  
    > [!NOTE]
    >  Certifique\-se de que os GUIDs são novas e exclusivas; caso contrário, o componente COM pode entrar em conflito com outros componentes COM.  
  
7.  Adicione o atributo `ComClass` para `ComClass1`, especificando os GUIDs para a identificação de classe, interface identificação e a identificação de eventos como no exemplo a seguir:  
  
     [!CODE [VbVbalrInterop#5](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrInterop#5)]  
  
8.  Classes COM devem ter um construtor `Public Sub New()` sem\-parâmetros, ou a classe não registrará corretamente.  Adicione um construtor sem\-parâmetros à classe:  
  
     [!CODE [VbVbalrInterop#6](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrInterop#6)]  
  
9. Adicione propriedades, métodos e eventos à classe, terminando\-lo com uma instrução `End Class`.  Selecione  **Build Solution** partir do  **Build** menu.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]cria o assembly e registra o objeto COM o sistema operacional.  
  
    > [!NOTE]
    >  Os objetos COM que você gerar com [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não podem ser usados por outros aplicativos [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] porque eles são objetos COM não é verdade.  Tenta adicionar referências a esses objetos COM irá gerar um erro.  Para obter detalhes, consulte:[Interoperabilidade COM em aplicativos .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.ComClassAttribute>   
 [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Instruções passo a passo: implementando a herança com objetos COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [Diretiva \#Region](../../../visual-basic/language-reference/directives/region-directive.md)   
 [Interoperabilidade COM em aplicativos .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)   
 [Solucionando problemas de interoperabilidade](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)