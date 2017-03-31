---
title: "-noconfig (Opções do compilador C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /noconfig
dev_langs:
- CSharp
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3fe7c90f8f5cdc3bb46fe2a762e211993b446072
ms.lasthandoff: 03/13/2017

---
# <a name="noconfig-c-compiler-options"></a>/noconfig (opções do compilador C#)
A opção **/noconfig** informa que o compilador não deve compilar com o arquivo csc.rsp, localizado no mesmo diretório que o arquivo csc.exe e carregado dele.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/noconfig  
```  
  
## <a name="remarks"></a>Comentários  
 O arquivo csc.rsp referencia todos os assemblies que acompanham o .NET Framework. As referências reais que o ambiente de desenvolvimento do Visual Studio .NET inclui dependem do tipo de projeto.  
  
 É possível modificar o arquivo csc.rsp e especificar opções do compilador adicionais que devem ser incluídas em cada compilação na linha de comando com csc.exe (exceto a opção **/noconfig**).  
  
 O compilador processa as opções passadas para o comando **csc** pela última vez. Portanto, qualquer opção na linha de comando substitui a configuração da mesma opção no arquivo csc.rsp.  
  
 Se você não desejar que o compilador procure e use as configurações no arquivo csc.rsp, especifique **/noconfig**.  
  
 Essa opção do compilador não está disponível no Visual Studio e não pode ser alterada programaticamente.  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB: como modificar as propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
