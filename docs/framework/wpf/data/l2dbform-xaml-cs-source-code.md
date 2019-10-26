---
title: Código-fonte de L2DBForm.xaml.cs
ms.date: 10/22/2019
ms.topic: sample
ms.openlocfilehash: 882699a76eab3c291cd92c298287bc5d28fb08e1
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920856"
---
# <a name="l2dbformxamlcs-source-code"></a><span data-ttu-id="a1ac5-102">Código-fonte de L2DBForm.xaml.cs</span><span class="sxs-lookup"><span data-stu-id="a1ac5-102">L2DBForm.xaml.cs source code</span></span>

<span data-ttu-id="a1ac5-103">Esta página contém o conteúdo e a descrição do C# código-fonte no arquivo *L2DBForm.XAML.cs*.</span><span class="sxs-lookup"><span data-stu-id="a1ac5-103">This page contains the contents and description of the C# source code in the file *L2DBForm.xaml.cs*.</span></span> <span data-ttu-id="a1ac5-104">A classe parcial de L2XDBForm contida neste arquivo pode ser dividida em três seções lógicas: membros de dados e o botão de `OnRemove` e de `OnAddBook` clique manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="a1ac5-104">The L2XDBForm partial class contained in this file can be divided into three logical sections: data members and the `OnRemove` and `OnAddBook` button click event handlers.</span></span>

## <a name="data-members"></a><span data-ttu-id="a1ac5-105">Membros de dados</span><span class="sxs-lookup"><span data-stu-id="a1ac5-105">Data members</span></span>

<span data-ttu-id="a1ac5-106">Dois membros de dados particulares são usados para associar essa classe aos recursos de janela usados em *L2DBForm.xaml*.</span><span class="sxs-lookup"><span data-stu-id="a1ac5-106">Two private data members are used to associate this class to the window resources used in *L2DBForm.xaml*.</span></span>

- <span data-ttu-id="a1ac5-107">O namespace `myBooks` variável é inicializada a `"http://www.mybooks.com"`.</span><span class="sxs-lookup"><span data-stu-id="a1ac5-107">The namespace variable `myBooks` is initialized to `"http://www.mybooks.com"`.</span></span>

- <span data-ttu-id="a1ac5-108">O membro `bookList` é inicializado no construtor para a cadeia de caracteres CDATA em *L2DBForm.xaml* com a seguinte linha:</span><span class="sxs-lookup"><span data-stu-id="a1ac5-108">The member `bookList` is initialized in the constructor to the CDATA string in *L2DBForm.xaml* with the following line:</span></span>

    ```csharp
    bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
    ```

## <a name="onaddbook-event-handler"></a><span data-ttu-id="a1ac5-109">Manipulador de eventos OnAddBook</span><span class="sxs-lookup"><span data-stu-id="a1ac5-109">OnAddBook event handler</span></span>

<span data-ttu-id="a1ac5-110">Este método contém as três declarações:</span><span class="sxs-lookup"><span data-stu-id="a1ac5-110">This method contains the following three statements:</span></span>

- <span data-ttu-id="a1ac5-111">A primeira declaração condicional é usada para validação de entrada.</span><span class="sxs-lookup"><span data-stu-id="a1ac5-111">The first conditional statement is used for input validation.</span></span>

- <span data-ttu-id="a1ac5-112">A segunda instrução cria um novo <xref:System.Xml.Linq.XElement> de valores de cadeia de caracteres que o usuário inseriu na seção de UI (interface do usuário) **Adicionar Novo Livro**.</span><span class="sxs-lookup"><span data-stu-id="a1ac5-112">The second statement creates a new <xref:System.Xml.Linq.XElement> from the string values the user entered in the **Add New Book** user interface (UI) section.</span></span>

- <span data-ttu-id="a1ac5-113">A última instrução adiciona esse novo elemento de livro ao provedor de dados em *L2DBForm.xaml*.</span><span class="sxs-lookup"><span data-stu-id="a1ac5-113">The last statement adds this new book element to the data provider in *L2DBForm.xaml*.</span></span> <span data-ttu-id="a1ac5-114">Portanto, a associação de dados dinâmicos atualizará automaticamente interface do usuário com esse novo item; nenhum código de acrescentar fornecido é necessário.</span><span class="sxs-lookup"><span data-stu-id="a1ac5-114">Consequently, dynamic data binding will automatically update the UI with this new item; no extra user-supplied code is required.</span></span>

## <a name="onremove-event-handler"></a><span data-ttu-id="a1ac5-115">Manipulador de eventos OnRemove</span><span class="sxs-lookup"><span data-stu-id="a1ac5-115">OnRemove event handler</span></span>

<span data-ttu-id="a1ac5-116">O manipulador de `OnRemove` é mais complicado que o manipulador de `OnAddBook` por dois motivos.</span><span class="sxs-lookup"><span data-stu-id="a1ac5-116">The `OnRemove` handler is more complicated than the `OnAddBook` handler for two reasons.</span></span> <span data-ttu-id="a1ac5-117">Primeiro, como o XML brutos contém o espaço em branco preservada, as novas linhas correspondentes também devem ser removidos com a entrada de livro.</span><span class="sxs-lookup"><span data-stu-id="a1ac5-117">First, because the raw XML contains preserved white space, matching newlines must also be removed with the book entry.</span></span> <span data-ttu-id="a1ac5-118">Segundo, como uma conveniência, a seleção, que estava no item excluído, é reiniciada a anterior na lista.</span><span class="sxs-lookup"><span data-stu-id="a1ac5-118">Second, as a convenience, the selection, which was on the deleted item, is reset to the previous one in the list.</span></span>

<span data-ttu-id="a1ac5-119">No entanto, o trabalho principal da remoção do item de livro selecionado é feito por apenas duas instruções:</span><span class="sxs-lookup"><span data-stu-id="a1ac5-119">However, the core work of removing the selected book item is accomplished by only two statements:</span></span>

- <span data-ttu-id="a1ac5-120">Primeiro, o elemento de livro associado com o item atualmente selecionado na caixa de listagem é recuperado:</span><span class="sxs-lookup"><span data-stu-id="a1ac5-120">First, the book element associated with the currently selected item in the list box is retrieved:</span></span>

    ```csharp
    XElement selBook = (XElement)lbBooks.SelectedItem;
    ```

- <span data-ttu-id="a1ac5-121">Em seguida, esse elemento é excluído do provedor de dados:</span><span class="sxs-lookup"><span data-stu-id="a1ac5-121">Then, this element is deleted from the data provider:</span></span>

    ```csharp
    selBook.Remove();
    ```

<span data-ttu-id="a1ac5-122">Além disso, a associação de dados dinâmicos garante que interface do usuário do programa é atualizado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="a1ac5-122">Again, dynamic data binding assures that the program's UI is automatically updated.</span></span>

## <a name="example"></a><span data-ttu-id="a1ac5-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a1ac5-123">Example</span></span>

### <a name="code"></a><span data-ttu-id="a1ac5-124">Código</span><span class="sxs-lookup"><span data-stu-id="a1ac5-124">Code</span></span>

```csharp
using System;
using System.Linq;
using System.Collections;
using System.Collections.Generic;
using System.Diagnostics;
using System.Text;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Input;
using System.Xml;
using System.Xml.Linq;

namespace LinqToXmlDataBinding {
    /// <summary>
    /// Interaction logic for L2XDBForm.xaml
    /// </summary>

    public partial class L2XDBForm : System.Windows.Window
    {
        XNamespace mybooks = "http://www.mybooks.com";
        XElement bookList;

        public L2XDBForm()
        {
            InitializeComponent();
            bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
        }

        void OnRemoveBook(object sender, EventArgs e)
        {
            int index = lbBooks.SelectedIndex;
            if (index < 0) return;

            XElement selBook = (XElement)lbBooks.SelectedItem;
            //Get next node before removing element.
            XNode nextNode = selBook.NextNode;
            selBook.Remove();

            //Remove any matching newline node.
            if (nextNode != null && nextNode.ToString().Trim().Equals(""))
            { nextNode.Remove(); }

            //Set selected item.
            if (lbBooks.Items.Count > 0)
            {  lbBooks.SelectedItem = lbBooks.Items[index > 0 ? index - 1 : 0]; }
        }

        void OnAddBook(object sender, EventArgs e)
        {
            if (String.IsNullOrEmpty(tbAddID.Text) ||
                String.IsNullOrEmpty(tbAddValue.Text))
            {
                MessageBox.Show("Please supply both a Book ID and a Value!", "Entry Error!");
                return;
            }
            XElement newBook = new XElement(
                                mybooks + "book",
                                new XAttribute("id", tbAddID.Text),
                                tbAddValue.Text);
            bookList.Add("  ", newBook, "\r\n");
        }
    }
}
```

### <a name="comments"></a><span data-ttu-id="a1ac5-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="a1ac5-125">Comments</span></span>

<span data-ttu-id="a1ac5-126">Para obter o código-fonte XAML associado a esses manipuladores, confira [Código-fonte de L2DBForm.xaml](l2dbform-xaml-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="a1ac5-126">For the associated XAML source for these handlers, see [L2DBForm.xaml source code](l2dbform-xaml-source-code.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a1ac5-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1ac5-127">See also</span></span>

- [<span data-ttu-id="a1ac5-128">Passo a passo: exemplo de LinqToXmlDataBinding</span><span class="sxs-lookup"><span data-stu-id="a1ac5-128">Walkthrough: LinqToXmlDataBinding example</span></span>](linq-to-xml-data-binding-sample.md)
- [<span data-ttu-id="a1ac5-129">Código-fonte de L2DBForm.xaml</span><span class="sxs-lookup"><span data-stu-id="a1ac5-129">L2DBForm.xaml source code</span></span>](l2dbform-xaml-source-code.md)
