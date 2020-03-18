---
title: Como construir LINQ para exemplos XML (C#)
ms.date: 07/20/2015
ms.assetid: e5d18fa1-2704-48fe-a44b-1564f97c9e9c
ms.openlocfilehash: 289a13daed7e3c871156bf50c6fa04c113c0cd13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141459"
---
# <a name="how-to-build-linq-to-xml-examples-c"></a><span data-ttu-id="619e4-102">Como construir LINQ para exemplos XML (C#)</span><span class="sxs-lookup"><span data-stu-id="619e4-102">How to build LINQ to XML examples (C#)</span></span>
<span data-ttu-id="619e4-103">Os vários snippets e exemplos nesta documentação usam classes e tipos de uma variedade de namespaces.</span><span class="sxs-lookup"><span data-stu-id="619e4-103">The various snippets and examples in this documentation use classes and types from a variety of namespaces.</span></span> <span data-ttu-id="619e4-104">Para compilar o código em C#, você precisará fornecer diretivas apropriadas de `using`.</span><span class="sxs-lookup"><span data-stu-id="619e4-104">When compiling C# code, you need to supply appropriate `using` directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="619e4-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="619e4-105">Example</span></span>  
 <span data-ttu-id="619e4-106">O código a seguir contém diretivas de `using` que os exemplos de C# exigem para compilar e executar.</span><span class="sxs-lookup"><span data-stu-id="619e4-106">The following code contains the `using` directives that the C# examples require to build and run.</span></span> <span data-ttu-id="619e4-107">Nem todas as diretivas de `using` são necessárias para todos os exemplos.</span><span class="sxs-lookup"><span data-stu-id="619e4-107">Not all `using` directives are required for every example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="619e4-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="619e4-108">See also</span></span>

- [<span data-ttu-id="619e4-109">Visão geral da programação LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="619e4-109">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
