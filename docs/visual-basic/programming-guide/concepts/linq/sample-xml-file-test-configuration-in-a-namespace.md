---
title: 'Arquivo XML de exemplo: Configuração de teste em um Namespace3'
ms.date: 07/20/2015
ms.assetid: aff02614-30ee-45e1-bc0f-d64b193d20b8
ms.openlocfilehash: 2a572bb4d2618bdd6ef002389703ea63ee2ed21b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="sample-xml-file-test-configuration-in-a-namespace"></a><span data-ttu-id="1f70e-102">Arquivo XML de Exemplo: Configuração de teste em um namespace</span><span class="sxs-lookup"><span data-stu-id="1f70e-102">Sample XML File: Test Configuration in a Namespace</span></span>
<span data-ttu-id="1f70e-103">O arquivo XML a seguir é usado em vários exemplos na documentação do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1f70e-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="1f70e-104">Este é um arquivo de configuração de teste.</span><span class="sxs-lookup"><span data-stu-id="1f70e-104">This is a test configuration file.</span></span> <span data-ttu-id="1f70e-105">XML é em um namespace.</span><span class="sxs-lookup"><span data-stu-id="1f70e-105">The XML is in a namespace.</span></span>  
  
## <a name="testconfiginnamespacexml"></a><span data-ttu-id="1f70e-106">TestConfigInNamespace.xml</span><span class="sxs-lookup"><span data-stu-id="1f70e-106">TestConfigInNamespace.xml</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1f70e-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1f70e-107">See Also</span></span>  
 [<span data-ttu-id="1f70e-108">Documentos XML de exemplo (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="1f70e-108">Sample XML Documents (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)
