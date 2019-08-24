---
title: 'Como: criar um controle associado simples em um Windows Form'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: df87f00e6e03de67c3fb1adc28472c96f4a47ef4
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015626"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a><span data-ttu-id="43666-102">Como: Criar um controle de associação simples em um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="43666-102">How to: Create a simple-bound control on a Windows Form</span></span>

<span data-ttu-id="43666-103">Com a *associação simples*, é possível exibir um elemento de dados simples, como um valor de coluna de uma tabela de dados em um controle.</span><span class="sxs-lookup"><span data-stu-id="43666-103">With *simple binding*, you can display a single data element, such as a column value from a dataset table, in a control.</span></span> <span data-ttu-id="43666-104">Você pode associar de maneira simples qualquer propriedade de um controle a um valor de dados.</span><span class="sxs-lookup"><span data-stu-id="43666-104">You can simple-bind any property of a control to a data value.</span></span>

## <a name="to-simple-bind-a-control"></a><span data-ttu-id="43666-105">Para associar de maneira simples um controle</span><span class="sxs-lookup"><span data-stu-id="43666-105">To simple-bind a control</span></span>

1. <span data-ttu-id="43666-106">Conecte-se a uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="43666-106">Connect to a data source.</span></span> <span data-ttu-id="43666-107">Para obter mais informações, consulte [Conectando a uma fonte de dados](../data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="43666-107">For more information, see [Connecting to a Data Source](../data/adonet/connecting-to-a-data-source.md).</span></span>

2. <span data-ttu-id="43666-108">No Visual Studio, selecione o controle no formulário e exiba a janela **Propriedades** .</span><span class="sxs-lookup"><span data-stu-id="43666-108">In Visual Studio, select the control on the form and display the **Properties** window.</span></span>

3. <span data-ttu-id="43666-109">Expanda a propriedade **(DataBindings)** .</span><span class="sxs-lookup"><span data-stu-id="43666-109">Expand the **(DataBindings)** property.</span></span>

     <span data-ttu-id="43666-110">As propriedades geralmente mais associadas são exibidas sob a propriedade **(DataBindings)** .</span><span class="sxs-lookup"><span data-stu-id="43666-110">The properties most often bound are displayed underneath the **(DataBindings)** property.</span></span> <span data-ttu-id="43666-111">Por exemplo, na maioria dos controles, a propriedade **Text** é vinculada com mais frequência.</span><span class="sxs-lookup"><span data-stu-id="43666-111">For example, in most controls, the **Text** property is most frequently bound.</span></span>

4. <span data-ttu-id="43666-112">Se a propriedade que você deseja associar não for uma das propriedades geralmente associadas, clique no botão de reticências![(o botão de reticências (...) na janela Propriedades do Visual](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png)Studio.) na caixa **(avançado)** para exibir o  **Caixa de diálogo formatação e Associação avançada** com uma lista completa de propriedades para esse controle.</span><span class="sxs-lookup"><span data-stu-id="43666-112">If the property you want to bind is not one of the commonly bound properties, click the **Ellipsis** button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png)) in the **(Advanced)** box to display the **Formatting and Advanced Binding** dialog box with a complete list of properties for that control.</span></span>

5. <span data-ttu-id="43666-113">Selecione a propriedade que deseja associar e clique na seta suspensa em **Associação**.</span><span class="sxs-lookup"><span data-stu-id="43666-113">Select the property you want to bind and click the drop-down arrow under **Binding**.</span></span>

     <span data-ttu-id="43666-114">Uma lista de fontes de dados disponíveis é exibida.</span><span class="sxs-lookup"><span data-stu-id="43666-114">A list of available data sources is displayed.</span></span>

6. <span data-ttu-id="43666-115">Expanda a fonte de dados a que deseja associar até encontrar o elemento de dados individual desejado.</span><span class="sxs-lookup"><span data-stu-id="43666-115">Expand the data source you want to bind to until you find the single data element you want.</span></span> <span data-ttu-id="43666-116">Por exemplo, se você estiver associando a um valor de coluna na tabela do conjunto de dados, expanda o nome do conjunto de dados e o nome da tabela para exibir os nomes das colunas.</span><span class="sxs-lookup"><span data-stu-id="43666-116">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>

7. <span data-ttu-id="43666-117">Clique no nome de um elemento que receberá a associação.</span><span class="sxs-lookup"><span data-stu-id="43666-117">Click the name of an element to bind to.</span></span>

8. <span data-ttu-id="43666-118">Se você estiver trabalhando na caixa de diálogo **Formatação e associação avançada**, clique em **OK** para voltar para a janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="43666-118">If you were working in the **Formatting and Advanced Binding** dialog box, click **OK** to return to the **Properties** window.</span></span>

9. <span data-ttu-id="43666-119">Se deseja associar propriedades adicionais do controle, repita as etapas 3 a 7.</span><span class="sxs-lookup"><span data-stu-id="43666-119">If you want to bind additional properties of the control, repeat steps 3 through 7.</span></span>

    > [!NOTE]
    > <span data-ttu-id="43666-120">Como controles de associação simples mostram apenas um elemento de dados, é muito comum incluir a lógica de navegação em um Windows Form com controles de associação simples.</span><span class="sxs-lookup"><span data-stu-id="43666-120">Because simple-bound controls show only a single data element, it is very typical to include navigation logic in a Windows Form with simple-bound controls.</span></span>

## <a name="see-also"></a><span data-ttu-id="43666-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43666-121">See also</span></span>

- <xref:System.Windows.Forms.Binding>
- [<span data-ttu-id="43666-122">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="43666-122">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
- [<span data-ttu-id="43666-123">Vinculação de dados e os Windows Forms</span><span class="sxs-lookup"><span data-stu-id="43666-123">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)
