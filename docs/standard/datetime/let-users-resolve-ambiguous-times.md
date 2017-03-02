---
title: "Como permitir que os usuários resolvam horários ambíguos"
description: "Como permitir que os usuários resolvam horários ambíguos"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: d6858a5c-02ab-4367-9e08-fa22c051c38d
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: ede8d021a4f524cf37f7ad00b6aed89d1b1729f8
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-let-users-resolve-ambiguous-times"></a>Como permitir que os usuários resolvam horários ambíguos

Um horário ambíguo é um horário que aponta para mais de um UTC (Tempo Universal Coordenado). Ocorre quando o horário do relógio é atrasado, como durante a transição do horário de verão de um fuso horário para seu horário padrão. Ao processar um horário ambíguo, você pode executar uma das seguintes ações:

* Se o horário ambíguo for um item de dados inserido pelo usuário, você pode deixar que o usuário resolva a ambiguidade.

* Faça uma suposição de como o tempo aponta para o UTC. Por exemplo, você pode supor que um horário ambíguo é sempre expresso no horário padrão do fuso horário.

Este artigo mostra como permitir que um usuário resolva um horário ambíguo.

## <a name="to-let-a-user-resolve-an-ambiguous-time"></a>Permitir que o usuário resolva um horário ambíguo

1. Obtenha a entrada de data e hora do usuário.

2. Chame o método [IsAmbiguousTime(DateTime)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTime)) ou [IsAmbiguousTime(DateTimeOffset)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTimeOffset)) para determinar se o horário é ambíguo.

3. Permita que o usuário selecione o deslocamento desejado.

4. Obtenha a data e hora de UTC subtraindo o deslocamento selecionado pelo usuário do horário local.

5. Chame o método `static` (`Shared` no Visual Basic ) [SpecifyKind](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) para definir a propriedade [Kind](xref:System.DateTime.Kind) do valor de data e hora do UTC como [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).

## <a name="example"></a>Exemplo

O exemplo a seguir solicita que o usuário insira uma data e hora e, se ela for ambígua, permite que o usuário selecione o horário UTC para o qual o horário ambíguo aponta. O exemplo usa um objeto [DateTime](xref:System.DateTime); você pode substituir um [DateTimeOffset](xref:System.DateTimeOffset) se desejar.

```csharp
private void GetUserDateInput()
{
   // Get date and time from user
   DateTime inputDate = GetUserDateTime();
   DateTime utcDate;

   // Exit if date has no significant value
   if (inputDate == DateTime.MinValue) return;

   if (TimeZoneInfo.Local.IsAmbiguousTime(inputDate))
   {
      Console.WriteLine("The date you've entered is ambiguous.");
      Console.WriteLine("Please select the correct offset from Universal Coordinated Time:");
      TimeSpan[] offsets = TimeZoneInfo.Local.GetAmbiguousTimeOffsets(inputDate);
      for (int ctr = 0; ctr < offsets.Length; ctr++)
      {
         Console.WriteLine("{0}.) {1} hours, {2} minutes", ctr, offsets[ctr].Hours, offsets[ctr].Minutes);
      }
      Console.Write("> ");
      int selection = Convert.ToInt32(Console.ReadLine());

      // Convert local time to UTC, and set Kind property to DateTimeKind.Utc
      utcDate = DateTime.SpecifyKind(inputDate - offsets[selection], DateTimeKind.Utc);

      Console.WriteLine("{0} local time corresponds to {1} {2}.", inputDate, utcDate, utcDate.Kind.ToString());
   }
   else
   {
      utcDate = inputDate.ToUniversalTime();
      Console.WriteLine("{0} local time corresponds to {1} {2}.", inputDate, utcDate, utcDate.Kind.ToString());    
   }
}

private DateTime GetUserDateTime() 
{
   bool exitFlag = false;             // flag to exit loop if date is valid
   string dateString;  
   DateTime inputDate = DateTime.MinValue;

   Console.Write("Enter a local date and time: ");
   while (! exitFlag)
   {
      dateString = Console.ReadLine();
      if (dateString.ToUpper() == "E")
         exitFlag = true;

      if (DateTime.TryParse(dateString, out inputDate))
         exitFlag = true;
      else
         Console.Write("Enter a valid date and time, or enter 'e' to exit: ");
   }

   return inputDate;        
}
```

```vb
Private Sub GetUserDateInput()
   ' Get date and time from user
   Dim inputDate As Date = GetUserDateTime()
   Dim utcDate As Date

   ' Exit if date has no significant value
   If inputDate = Date.MinValue Then Exit Sub

   If TimeZoneInfo.Local.IsAmbiguousTime(inputDate) Then
      Console.WriteLine("The date you've entered is ambiguous.")
      Console.WriteLine("Please select the correct offset from Universal Coordinated Time:")
      Dim offsets() As TimeSpan = TimeZoneInfo.Local.GetAmbiguousTimeOffsets(inputDate)
      For ctr As Integer = 0 to offsets.Length - 1
         Dim zoneDescription As String
         If offsets(ctr).Equals(TimeZoneInfo.Local.BaseUtcOffset) Then 
            zoneDescription = TimeZoneInfo.Local.StandardName
         Else
            zoneDescription = TimeZoneInfo.Local.DaylightName
         End If
         Console.WriteLine("{0}.) {1} hours, {2} minutes ({3})", _
                           ctr, offsets(ctr).Hours, offsets(ctr).Minutes, zoneDescription)
      Next         
      Console.Write("> ")
      Dim selection As Integer = CInt(Console.ReadLine())

      ' Convert local time to UTC, and set Kind property to DateTimeKind.Utc
      utcDate = Date.SpecifyKind(inputDate - offsets(selection), DateTimeKind.Utc)

      Console.WriteLine("{0} local time corresponds to {1} {2}.", inputDate, utcDate, utcDate.Kind.ToString())
   Else
      utcDate = inputDate.ToUniversalTime()
      Console.WriteLine("{0} local time corresponds to {1} {2}.", inputDate, utcDate, utcDate.Kind.ToString())    
   End If
End Sub

Private Function GetUserDateTime() As Date
   Dim exitFlag As Boolean = False            ' flag to exit loop if date is valid
   Dim dateString As String 
   Dim inputDate As Date = Date.MinValue

   Console.Write("Enter a local date and time: ")
   Do While Not exitFlag
      dateString = Console.ReadLine()
      If dateString.ToUpper = "E" Then exitFlag = True
      If Date.TryParse(dateString, inputDate) Then
         exitFlag = true
      Else   
         Console.Write("Enter a valid date and time, or enter 'e' to exit: ")
      End If
   Loop

   Return inputDate        
End Function
```

O núcleo do código de exemplo usa uma matriz de objetos [TimeSpan](xref:System.TimeSpan) para indicar possíveis deslocamentos de horário ambíguo do UTC. No entanto, esses deslocamentos provavelmente não serão significativos para o usuário. Para esclarecer o significado dos deslocamentos, o código também observa se um deslocamento representa o horário padrão do fuso horário local ou seu horário de verão. O código determina qual horário é padrão e qual é o de verão comparando o deslocamento com o valor da propriedade [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset). Essa propriedade indica a diferença entre o UTC e o horário padrão do fuso horário.

Neste exemplo, todas as referências ao fuso horário local são feitas através da propriedade [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local); o fuso horário local nunca é atribuído a uma variável de objeto. Essa é uma prática recomendada porque outra chamada poderia limpar os dados em cache e invalidar todos os objetos aos quais o fuso horário local é atribuído.

## <a name="see-also"></a>Consulte também

[Datas, horas e fusos horários](index.md)

[Como resolver horários ambíguos](resolve-ambiguous-times.md)


