---
title: 'Como: Criar um objeto de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataObject class [WPF], creating
- data objects [WPF], creating
- drag-and-drop [WPF], creating data objects
ms.assetid: 022fa142-717d-4fea-a53c-3b52e9d91aff
ms.openlocfilehash: f7bdfbf3dba0c700513348195c1d031d4c2c8b65
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370586"
---
# <a name="how-to-create-a-data-object"></a><span data-ttu-id="8a929-102">Como: Criar um objeto de dados</span><span class="sxs-lookup"><span data-stu-id="8a929-102">How to: Create a Data Object</span></span>
<span data-ttu-id="8a929-103">Os exemplos a seguir mostram várias maneiras de criar um objeto de dados usando os construtores fornecidos pela <xref:System.Windows.DataObject> classe.</span><span class="sxs-lookup"><span data-stu-id="8a929-103">The following examples show various ways to create a data object using the constructors provided by the <xref:System.Windows.DataObject> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a929-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8a929-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="8a929-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a929-105">Description</span></span>  
 <span data-ttu-id="8a929-106">O exemplo de código a seguir cria um novo objeto de dados e usa um dos construtores sobrecarregados (<xref:System.Windows.DataObject.%23ctor%28System.Object%29>) para inicializar o objeto de dados com uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8a929-106">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.Object%29>) to initialize the data object with a string.</span></span>  <span data-ttu-id="8a929-107">Neste caso, um formato de dados apropriado é determinado automaticamente de acordo com o tipo de dados armazenado e a conversão automática dos dados armazenados é permitida por padrão.</span><span class="sxs-lookup"><span data-stu-id="8a929-107">In this case, an appropriate data format is determined automatically according to the stored data's type, and auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8a929-108">Código</span><span class="sxs-lookup"><span data-stu-id="8a929-108">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple)]  
  
### <a name="description"></a><span data-ttu-id="8a929-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a929-109">Description</span></span>  
 <span data-ttu-id="8a929-110">O código de exemplo a seguir é uma versão condensada do código mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="8a929-110">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8a929-111">Código</span><span class="sxs-lookup"><span data-stu-id="8a929-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple_condensed)]  
  
## <a name="example"></a><span data-ttu-id="8a929-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8a929-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="8a929-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a929-113">Description</span></span>  
 <span data-ttu-id="8a929-114">O exemplo de código a seguir cria um novo objeto de dados e usa um dos construtores sobrecarregados (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>) para inicializar o objeto de dados com uma cadeia de caracteres e um formato de dados especificado.</span><span class="sxs-lookup"><span data-stu-id="8a929-114">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="8a929-115">Nesse caso, o formato de dados é especificado por uma cadeia de caracteres; o <xref:System.Windows.DataFormats> classe fornece um conjunto de cadeias de caracteres de tipo previamente definido.</span><span class="sxs-lookup"><span data-stu-id="8a929-115">In this case the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="8a929-116">A conversão automática dos dados armazenados é permitida por padrão.</span><span class="sxs-lookup"><span data-stu-id="8a929-116">Auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8a929-117">Código</span><span class="sxs-lookup"><span data-stu-id="8a929-117">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
### <a name="description"></a><span data-ttu-id="8a929-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a929-118">Description</span></span>  
 <span data-ttu-id="8a929-119">O código de exemplo a seguir é uma versão condensada do código mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="8a929-119">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8a929-120">Código</span><span class="sxs-lookup"><span data-stu-id="8a929-120">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring_condensed)]  
  
## <a name="example"></a><span data-ttu-id="8a929-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8a929-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="8a929-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a929-122">Description</span></span>  
 <span data-ttu-id="8a929-123">O exemplo de código a seguir cria um novo objeto de dados e usa um dos construtores sobrecarregados (<xref:System.Windows.DataObject.%23ctor%2A>) para inicializar o objeto de dados com uma cadeia de caracteres e um formato de dados especificado.</span><span class="sxs-lookup"><span data-stu-id="8a929-123">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%2A>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="8a929-124">Nesse caso, o formato de dados é especificado por um <xref:System.Type> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8a929-124">In this case the data format is specified by a <xref:System.Type> parameter.</span></span>  <span data-ttu-id="8a929-125">A conversão automática dos dados armazenados é permitida por padrão.</span><span class="sxs-lookup"><span data-stu-id="8a929-125">Auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8a929-126">Código</span><span class="sxs-lookup"><span data-stu-id="8a929-126">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type)]  
  
### <a name="description"></a><span data-ttu-id="8a929-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a929-127">Description</span></span>  
 <span data-ttu-id="8a929-128">O código de exemplo a seguir é uma versão condensada do código mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="8a929-128">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8a929-129">Código</span><span class="sxs-lookup"><span data-stu-id="8a929-129">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type_condensed)]  
  
## <a name="example"></a><span data-ttu-id="8a929-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8a929-130">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="8a929-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a929-131">Description</span></span>  
 <span data-ttu-id="8a929-132">O exemplo de código a seguir cria um novo objeto de dados e usa um dos construtores sobrecarregados (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>) para inicializar o objeto de dados com uma cadeia de caracteres e um formato de dados especificado.</span><span class="sxs-lookup"><span data-stu-id="8a929-132">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="8a929-133">Nesse caso, o formato de dados é especificado por uma cadeia de caracteres; o <xref:System.Windows.DataFormats> classe fornece um conjunto de cadeias de caracteres de tipo previamente definido.</span><span class="sxs-lookup"><span data-stu-id="8a929-133">In this case the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="8a929-134">Essa sobrecarga do construtor em particular permite que o autor da chamada especifique se a conversão automática é permitida.</span><span class="sxs-lookup"><span data-stu-id="8a929-134">This particular constructor overload enables the caller to specify whether auto-converting is allowed.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8a929-135">Código</span><span class="sxs-lookup"><span data-stu-id="8a929-135">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert)]  
  
### <a name="description"></a><span data-ttu-id="8a929-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a929-136">Description</span></span>  
 <span data-ttu-id="8a929-137">O código de exemplo a seguir é uma versão condensada do código mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="8a929-137">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8a929-138">Código</span><span class="sxs-lookup"><span data-stu-id="8a929-138">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert_condensed)]  
  
## <a name="see-also"></a><span data-ttu-id="8a929-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a929-139">See also</span></span>
- <xref:System.Windows.IDataObject>
