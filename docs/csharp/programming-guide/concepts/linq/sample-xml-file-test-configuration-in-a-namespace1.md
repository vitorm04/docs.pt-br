---
title: 'Arquivo XML de exemplo: configuração de teste em um namespace1'
ms.date: 07/20/2015
ms.assetid: e75ad1bc-5636-4623-9a34-a286a8c485d6
ms.openlocfilehash: 01470a66ac42eb9fd68fdcde0d0a4bf9150e3d5f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506495"
---
# <a name="sample-xml-file-test-configuration-in-a-namespace"></a><span data-ttu-id="3f6b3-102">Arquivo XML de Exemplo: Configuração de teste em um namespace</span><span class="sxs-lookup"><span data-stu-id="3f6b3-102">Sample XML File: Test Configuration in a Namespace</span></span>
<span data-ttu-id="3f6b3-103">O arquivo XML a seguir é usado em vários exemplos na documentação do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f6b3-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="3f6b3-104">Este é um arquivo de configuração de teste.</span><span class="sxs-lookup"><span data-stu-id="3f6b3-104">This is a test configuration file.</span></span> <span data-ttu-id="3f6b3-105">XML é em um namespace.</span><span class="sxs-lookup"><span data-stu-id="3f6b3-105">The XML is in a namespace.</span></span>  
  
## <a name="testconfiginnamespacexml"></a><span data-ttu-id="3f6b3-106">TestConfigInNamespace.xml</span><span class="sxs-lookup"><span data-stu-id="3f6b3-106">TestConfigInNamespace.xml</span></span>  
  
```xml  
<?xml version="1.0"?>  
<Tests xmlns="http://www.adatum.com">  
  <Test TestId="0001" TestType="CMD">  
    <Name>Convert number to string</Name>  
    <CommandLine>Examp1.EXE</CommandLine>  
    <Input>1</Input>  
    <Output>One</Output>  
  </Test>  
  <Test TestId="0002" TestType="CMD">  
    <Name>Find succeeding characters</Name>  
    <CommandLine>Examp2.EXE</CommandLine>  
    <Input>abc</Input>  
    <Output>def</Output>  
  </Test>  
  <Test TestId="0003" TestType="GUI">  
    <Name>Convert multiple numbers to strings</Name>  
    <CommandLine>Examp2.EXE /Verbose</CommandLine>  
    <Input>123</Input>  
    <Output>One Two Three</Output>  
  </Test>  
  <Test TestId="0004" TestType="GUI">  
    <Name>Find correlated key</Name>  
    <CommandLine>Examp3.EXE</CommandLine>  
    <Input>a1</Input>  
    <Output>b1</Output>  
  </Test>  
  <Test TestId="0005" TestType="GUI">  
    <Name>Count characters</Name>  
    <CommandLine>FinalExamp.EXE</CommandLine>  
    <Input>This is a test</Input>  
    <Output>14</Output>  
  </Test>  
  <Test TestId="0006" TestType="GUI">  
    <Name>Another Test</Name>  
    <CommandLine>Examp2.EXE</CommandLine>  
    <Input>Test Input</Input>  
    <Output>10</Output>  
  </Test>  
</Tests>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f6b3-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f6b3-107">See Also</span></span>

- [<span data-ttu-id="3f6b3-108">Documentos XML de exemplo (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="3f6b3-108">Sample XML Documents (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)
