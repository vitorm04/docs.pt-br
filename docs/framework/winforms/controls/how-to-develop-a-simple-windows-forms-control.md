---
title: 'Como: Desenvolver um controle simples do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
ms.openlocfilehash: a190d86f5ebe258427ac4a73c16c7f271462b69c
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63807910"
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a>Como: Desenvolver um controle simples do Windows Forms

Esta seção explica as etapas principais para a criação de um controle personalizado dos Windows Forms. O controle simples desenvolvido neste passo a passo permite que o alinhamento de seu <xref:System.Windows.Forms.Control.Text%2A> propriedade a ser alterada. Ele não gera ou manipula eventos.

### <a name="to-create-a-simple-custom-control"></a>Para criar um controle personalizado simples

1. Defina uma classe derivada de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.

    ```vb
    Public Class FirstControl
       Inherits Control

    End Class
    ```

    ```csharp
    public class FirstControl:Control {}
    ```

2. Defina as propriedades. (Não é necessário para definir propriedades, como um controle herda muitas propriedades do <xref:System.Windows.Forms.Control> classe, mas a maioria dos controles personalizados geralmente define propriedades adicionais.) O fragmento de código a seguir define uma propriedade chamada `TextAlignment` que `FirstControl` usa para formatar a exibição da <xref:System.Windows.Forms.Control.Text%2A> propriedade herdada de <xref:System.Windows.Forms.Control>. Para obter mais informações sobre como definir as propriedades, consulte [Properties Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v%3dvs.120)) (Visão geral das propriedades).

     [!code-csharp[System.Windows.Forms.FirstControl#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]

     Quando você define uma propriedade que altera a exibição visual do controle, você deve chamar o <xref:System.Windows.Forms.Control.Invalidate%2A> método para redesenhar o controle. <xref:System.Windows.Forms.Control.Invalidate%2A> é definido na classe base <xref:System.Windows.Forms.Control>.

3. Substituir o protegido <xref:System.Windows.Forms.Control.OnPaint%2A> método herdado do <xref:System.Windows.Forms.Control> para fornecer a lógica de renderização para o seu controle. Se você não substituir <xref:System.Windows.Forms.Control.OnPaint%2A>, seu controle não será possível desenhar a mesmo. No fragmento de código a seguir, o <xref:System.Windows.Forms.Control.OnPaint%2A> método exibe a <xref:System.Windows.Forms.Control.Text%2A> propriedade herdada de <xref:System.Windows.Forms.Control> com o alinhamento especificado pelo `alignmentValue` campo.

     [!code-csharp[System.Windows.Forms.FirstControl#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]

4. Forneça atributos para o seu controle. Os atributos permitem que um designer visual exiba adequadamente seu controle, suas propriedades e eventos no tempo de design. O fragmento de código a seguir se aplica aos atributos para a propriedade `TextAlignment`. Em um designer como o Visual Studio, o <xref:System.ComponentModel.CategoryAttribute.Category%2A> atributo (mostrado no fragmento de código) faz com que a propriedade a ser exibida em uma categoria lógica. O <xref:System.ComponentModel.DescriptionAttribute.Description%2A> atributo faz com que uma cadeia de caracteres descritiva a ser exibido na parte inferior a **propriedades** janela quando o `TextAlignment` propriedade for selecionada. Para obter mais informações sobre atributos, consulte [Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)) (Atributos de tempo de design para componentes).

     [!code-csharp[System.Windows.Forms.FirstControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]

5. (opcional) Forneça recursos para o seu controle. Você pode fornecer um recurso, como um bitmap, para seu controle usando uma opção do compilador (`/res` para C#) para recursos de pacote com seu controle. Em tempo de execução, o recurso pode ser recuperado usando os métodos do <xref:System.Resources.ResourceManager> classe. Para obter mais informações sobre a criação e o uso de recursos, consulte [Resources in Desktop Apps](../../resources/index.md) (Recursos em aplicativos da Área de Trabalho).

6. Compile e implante seu controle. Para compilar e implantar `FirstControl,`, execute as seguintes etapas:

    1. Salve o código no exemplo a seguir em um arquivo de origem (como FirstControl.cs ou FirstControl.vb).

    2. Compile o código-fonte em um assembly e salve-o no diretório do aplicativo. Para fazer isso, execute o seguinte comando do diretório que contém o arquivo de origem.

        ```console
        vbc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.vb
        ```

        ```console
        csc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.cs
        ```

         A opção do compilador `/t:library` informa o compilador que o assembly que você está criando é uma biblioteca (e não um executável). A opção `/out` especifica o caminho e o nome do assembly. A opção `/r` fornece o nome dos assemblies referenciados pelo seu código. Neste exemplo, você cria um assembly particular que somente os seus aplicativos podem usar. Portanto, você precisa salvá-lo no diretório do aplicativo. Para obter mais informações sobre o empacotamento e a implantação de um controle para distribuição, consulte [Implantação](../../deployment/index.md).

O exemplo a seguir mostra o código para `FirstControl`. O controle é colocado no namespace `CustomWinControls`. Um namespace fornece um agrupamento lógico de tipos relacionados. Você pode criar seu controle em um namespace novo ou existente. Em C#, a declaração `using` (no Visual Basic, `Imports`) permite que os tipos sejam acessados de um namespace sem usar o nome totalmente qualificado do tipo. No exemplo a seguir, o `using` declaração permite que o código acessar a classe <xref:System.Windows.Forms.Control> partir <xref:System.Windows.Forms?displayProperty=nameWithType> simplesmente <xref:System.Windows.Forms.Control> em vez de ter que usar o nome totalmente qualificado <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.

[!code-csharp[System.Windows.Forms.FirstControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
[!code-vb[System.Windows.Forms.FirstControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]

## <a name="using-the-custom-control-on-a-form"></a>Usando o controle personalizado em um formulário

O exemplo a seguir mostra um formulário simples que usa `FirstControl`. Ele cria três instâncias de `FirstControl`, cada uma com um valor diferente para a propriedade `TextAlignment`.

#### <a name="to-compile-and-run-this-sample"></a>Para compilar e executar esse exemplo

1. Salve o código no exemplo a seguir em um arquivo de origem (SimpleForm.cs ou SimpleForms.vb).

2. Compile o código-fonte em um assembly executável, executando o seguinte comando do diretório que contém o arquivo de origem.

    ```console
    vbc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.vb
    ```

    ```console
    csc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.cs
    ```

     Customwincontrols é o assembly que contém a classe `FirstControl`. Esse assembly deve estar no mesmo diretório que o arquivo de origem para o formulário que o acessa (SimpleForm.cs ou SimpleForms.vb).

3. Execute SimpleForm.exe usando o seguinte comando.

    ```console
    SimpleForm
    ```

[!code-csharp[System.Windows.Forms.FirstControl#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
[!code-vb[System.Windows.Forms.FirstControl#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]

## <a name="see-also"></a>Consulte também

- [Propriedades em controles do Windows Forms](properties-in-windows-forms-controls.md)
- [Eventos em controles do Windows Forms](events-in-windows-forms-controls.md)
