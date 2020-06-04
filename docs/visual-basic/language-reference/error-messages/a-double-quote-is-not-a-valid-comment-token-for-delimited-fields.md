---
title: Aspas duplas não formam um token de comentário válido para campos delimitados em que EscapeQuote esteja definido como True
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_InvalidComment
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
ms.openlocfilehash: a66d43d249a12ffa552073866f2e0a1e6d453608
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409927"
---
# <a name="a-double-quote-is-not-a-valid-comment-token-for-delimited-fields-where-escapequote-is-set-to-true"></a><span data-ttu-id="f865b-102">Aspas duplas não formam um token de comentário válido para campos delimitados em que EscapeQuote esteja definido como True</span><span class="sxs-lookup"><span data-stu-id="f865b-102">A double quote is not a valid comment token for delimited fields where EscapeQuote is set to True</span></span>

<span data-ttu-id="f865b-103">Uma aspa foi fornecida como o delimitador para o `TextFieldParser` , mas `EscapeQuotes` está definida como `True` .</span><span class="sxs-lookup"><span data-stu-id="f865b-103">A quotation mark has been supplied as the delimiter for the `TextFieldParser`, but `EscapeQuotes` is set to `True`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f865b-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f865b-104">To correct this error</span></span>  
  
- <span data-ttu-id="f865b-105">Defina `EscapeQuotes` como `False`.</span><span class="sxs-lookup"><span data-stu-id="f865b-105">Set `EscapeQuotes` to `False`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f865b-106">Confira também</span><span class="sxs-lookup"><span data-stu-id="f865b-106">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>
- [<span data-ttu-id="f865b-107">Como: ler de arquivos de texto separados por vírgula</span><span class="sxs-lookup"><span data-stu-id="f865b-107">How to: Read From Comma-Delimited Text Files</span></span>](../../developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
