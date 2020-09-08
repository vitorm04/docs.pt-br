---
title: Como criar exemplos de LINQ to XML
description: O código C# e Visual Basic nesta documentação usa classes e tipos de vários namespaces. Para compilar e executar o código, você deve fornecer as diretivas e instruções apropriadas para acessar os namespaces.
ms.date: 07/20/2015
ms.assetid: e5d18fa1-2704-48fe-a44b-1564f97c9e9c
ms.openlocfilehash: 94b2368e2c861f84d7db08fbbba57ef0f0da4d40
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551890"
---
# <a name="how-to-build-linq-to-xml-examples"></a><span data-ttu-id="7b05d-104">Como criar exemplos de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="7b05d-104">How to build LINQ to XML examples</span></span>

<span data-ttu-id="7b05d-105">Os trechos de código e os exemplos nesta documentação usam classes e tipos de vários namespaces.</span><span class="sxs-lookup"><span data-stu-id="7b05d-105">The snippets and examples in this documentation use classes and types from various namespaces.</span></span> <span data-ttu-id="7b05d-106">Ao compilar o código C#, você precisa fornecer as `using` diretivas apropriadas e, ao compilar Visual Basic código, precisa fornecer `Imports` instruções apropriadas.</span><span class="sxs-lookup"><span data-stu-id="7b05d-106">When compiling C# code you need to supply appropriate `using` directives, and when compiling Visual Basic code you need to supply appropriate `Imports` statements.</span></span>

## <a name="example"></a><span data-ttu-id="7b05d-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7b05d-107">Example</span></span>

<span data-ttu-id="7b05d-108">O código a seguir contém diretivas de `using` que os exemplos de C# exigem para compilar e executar.</span><span class="sxs-lookup"><span data-stu-id="7b05d-108">The following code contains the `using` directives that the C# examples require to build and run.</span></span> <span data-ttu-id="7b05d-109">Nem todas as diretivas de `using` são necessárias para todos os exemplos.</span><span class="sxs-lookup"><span data-stu-id="7b05d-109">Not all `using` directives are required for every example.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Collections;
using System.Collections.Generic;
using System.Collections.Specialized;
using System.Text;
using System.Linq;
using System.Xml;
using System.Xml.Linq;
using System.Xml.Schema;
using System.Xml.XPath;
using System.Xml.Xsl;
using System.IO;
using System.Threading;
using System.Reflection;
using System.IO.Packaging;
```

<span data-ttu-id="7b05d-110">O código a seguir contém instruções de `Imports` que os exemplos de Visual Basic exigem para compilar e executar.</span><span class="sxs-lookup"><span data-stu-id="7b05d-110">The following code contains the `Imports` statements that the Visual Basic examples require to build and run.</span></span> <span data-ttu-id="7b05d-111">Nem todas as instruções de `Imports` são necessárias para todos os exemplos.</span><span class="sxs-lookup"><span data-stu-id="7b05d-111">Not all `Imports` statements are required for every example.</span></span>

```vb
Imports System.Diagnostics
Imports System.Collections
Imports System.Collections.Generic
Imports System.Collections.Specialized
Imports System.Text
Imports System.Linq
Imports System.Xml
Imports System.Xml.Linq
Imports System.Xml.Schema
Imports System.Xml.XPath
Imports System.Xml.Xsl
Imports System.IO
Imports System.Threading
Imports System.Reflection
Imports System.IO.Packaging
```

## <a name="see-also"></a><span data-ttu-id="7b05d-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="7b05d-112">See also</span></span>

- [<span data-ttu-id="7b05d-113">Visão geral de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="7b05d-113">LINQ to XML overview</span></span>](linq-xml-overview.md)
