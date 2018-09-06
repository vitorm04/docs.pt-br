---
title: Coleções de esquema ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: bdedbb11960f02b99dcca6388abf663635238f74
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877525"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="dee0a-102">Coleções de esquema ODBC</span><span class="sxs-lookup"><span data-stu-id="dee0a-102">ODBC Schema Collections</span></span>
<span data-ttu-id="dee0a-103">Esta seção discute o suporte de coleção de esquema para os drivers ODBC para Microsoft SQL Server, Oracle e Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="dee0a-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="dee0a-104">Driver ODBC do Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="dee0a-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="dee0a-105">O Driver ODBC do Microsoft SQL Server suporta as seguintes coleções de esquema específico, além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="dee0a-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="dee0a-106">Tabelas</span><span class="sxs-lookup"><span data-stu-id="dee0a-106">Tables</span></span>  
  
-   <span data-ttu-id="dee0a-107">Índices</span><span class="sxs-lookup"><span data-stu-id="dee0a-107">Indexes</span></span>  
  
-   <span data-ttu-id="dee0a-108">Colunas</span><span class="sxs-lookup"><span data-stu-id="dee0a-108">Columns</span></span>  
  
-   <span data-ttu-id="dee0a-109">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="dee0a-109">Procedures</span></span>  
  
-   <span data-ttu-id="dee0a-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="dee0a-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="dee0a-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="dee0a-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="dee0a-112">Exibições</span><span class="sxs-lookup"><span data-stu-id="dee0a-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="dee0a-113">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="dee0a-113">Tables and Views</span></span>  
  
|<span data-ttu-id="dee0a-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="dee0a-114">ColumnName</span></span>|<span data-ttu-id="dee0a-115">DataType</span><span class="sxs-lookup"><span data-stu-id="dee0a-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dee0a-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="dee0a-116">TABLE_CAT</span></span>|<span data-ttu-id="dee0a-117">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-117">String</span></span>|  
|<span data-ttu-id="dee0a-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="dee0a-118">TABLE_SCHEM</span></span>|<span data-ttu-id="dee0a-119">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-119">String</span></span>|  
|<span data-ttu-id="dee0a-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-120">TABLE_NAME</span></span>|<span data-ttu-id="dee0a-121">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-121">String</span></span>|  
|<span data-ttu-id="dee0a-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-122">TABLE_TYPE</span></span>|<span data-ttu-id="dee0a-123">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-123">String</span></span>|  
|<span data-ttu-id="dee0a-124">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="dee0a-124">REMARKS</span></span>|<span data-ttu-id="dee0a-125">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="dee0a-126">Índices</span><span class="sxs-lookup"><span data-stu-id="dee0a-126">Indexes</span></span>  
  
|<span data-ttu-id="dee0a-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="dee0a-127">ColumnName</span></span>|<span data-ttu-id="dee0a-128">DataType</span><span class="sxs-lookup"><span data-stu-id="dee0a-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dee0a-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="dee0a-129">TABLE_CAT</span></span>|<span data-ttu-id="dee0a-130">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-130">String</span></span>|  
|<span data-ttu-id="dee0a-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="dee0a-131">TABLE_SCHEM</span></span>|<span data-ttu-id="dee0a-132">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-132">String</span></span>|  
|<span data-ttu-id="dee0a-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-133">TABLE_NAME</span></span>|<span data-ttu-id="dee0a-134">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-134">String</span></span>|  
|<span data-ttu-id="dee0a-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="dee0a-135">NON_UNIQUE</span></span>|<span data-ttu-id="dee0a-136">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-136">Int16</span></span>|  
|<span data-ttu-id="dee0a-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="dee0a-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="dee0a-138">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-138">String</span></span>|  
|<span data-ttu-id="dee0a-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-139">INDEX_NAME</span></span>|<span data-ttu-id="dee0a-140">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-140">String</span></span>|  
|<span data-ttu-id="dee0a-141">TIPO</span><span class="sxs-lookup"><span data-stu-id="dee0a-141">TYPE</span></span>|<span data-ttu-id="dee0a-142">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-142">Int16</span></span>|  
|<span data-ttu-id="dee0a-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dee0a-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="dee0a-144">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-144">Int16</span></span>|  
|<span data-ttu-id="dee0a-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-145">COLUMN_NAME</span></span>|<span data-ttu-id="dee0a-146">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-146">String</span></span>|  
|<span data-ttu-id="dee0a-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="dee0a-147">ASC_OR_DESC</span></span>|<span data-ttu-id="dee0a-148">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-148">String</span></span>|  
|<span data-ttu-id="dee0a-149">CARDINALIDADE</span><span class="sxs-lookup"><span data-stu-id="dee0a-149">CARDINATLITY</span></span>|<span data-ttu-id="dee0a-150">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-150">Int32</span></span>|  
|<span data-ttu-id="dee0a-151">PÁGINAS</span><span class="sxs-lookup"><span data-stu-id="dee0a-151">PAGES</span></span>|<span data-ttu-id="dee0a-152">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-152">Int32</span></span>|  
|<span data-ttu-id="dee0a-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="dee0a-153">FILTER_CONDITION</span></span>|<span data-ttu-id="dee0a-154">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-154">String</span></span>|  
|<span data-ttu-id="dee0a-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dee0a-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="dee0a-156">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-156">String</span></span>|  
|<span data-ttu-id="dee0a-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="dee0a-158">Byte</span><span class="sxs-lookup"><span data-stu-id="dee0a-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="dee0a-159">Colunas</span><span class="sxs-lookup"><span data-stu-id="dee0a-159">Columns</span></span>  
  
|<span data-ttu-id="dee0a-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="dee0a-160">ColumnName</span></span>|<span data-ttu-id="dee0a-161">DataType</span><span class="sxs-lookup"><span data-stu-id="dee0a-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dee0a-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="dee0a-162">TABLE_CAT</span></span>|<span data-ttu-id="dee0a-163">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-163">String</span></span>|  
|<span data-ttu-id="dee0a-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="dee0a-164">TABLE_SCHEM</span></span>|<span data-ttu-id="dee0a-165">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-165">String</span></span>|  
|<span data-ttu-id="dee0a-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-166">TABLE_NAME</span></span>|<span data-ttu-id="dee0a-167">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-167">String</span></span>|  
|<span data-ttu-id="dee0a-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-168">COLUMN_NAME</span></span>|<span data-ttu-id="dee0a-169">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-169">String</span></span>|  
|<span data-ttu-id="dee0a-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-170">DATA_TYPE</span></span>|<span data-ttu-id="dee0a-171">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-171">Int16</span></span>|  
|<span data-ttu-id="dee0a-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-172">TYPE_NAME</span></span>|<span data-ttu-id="dee0a-173">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-173">String</span></span>|  
|<span data-ttu-id="dee0a-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="dee0a-174">COLUMN_SIZE</span></span>|<span data-ttu-id="dee0a-175">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-175">Int32</span></span>|  
|<span data-ttu-id="dee0a-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dee0a-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="dee0a-177">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-177">Int32</span></span>|  
|<span data-ttu-id="dee0a-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="dee0a-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="dee0a-179">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-179">Int16</span></span>|  
|<span data-ttu-id="dee0a-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="dee0a-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="dee0a-181">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-181">Int16</span></span>|  
|<span data-ttu-id="dee0a-182">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="dee0a-182">NULLABLE</span></span>|<span data-ttu-id="dee0a-183">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-183">Int16</span></span>|  
|<span data-ttu-id="dee0a-184">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="dee0a-184">REMARKS</span></span>|<span data-ttu-id="dee0a-185">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-185">String</span></span>|  
|<span data-ttu-id="dee0a-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="dee0a-186">COLUMN_DEF</span></span>|<span data-ttu-id="dee0a-187">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-187">String</span></span>|  
|<span data-ttu-id="dee0a-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="dee0a-189">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-189">Int16</span></span>|  
|<span data-ttu-id="dee0a-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="dee0a-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="dee0a-191">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-191">Int16</span></span>|  
|<span data-ttu-id="dee0a-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dee0a-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="dee0a-193">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-193">Int32</span></span>|  
|<span data-ttu-id="dee0a-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dee0a-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="dee0a-195">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-195">Int32</span></span>|  
|<span data-ttu-id="dee0a-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="dee0a-196">IS_NULLABLE</span></span>|<span data-ttu-id="dee0a-197">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-197">String</span></span>|  
|<span data-ttu-id="dee0a-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dee0a-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="dee0a-199">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-199">String</span></span>|  
|<span data-ttu-id="dee0a-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dee0a-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="dee0a-201">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-201">String</span></span>|  
|<span data-ttu-id="dee0a-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="dee0a-203">Byte</span><span class="sxs-lookup"><span data-stu-id="dee0a-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="dee0a-204">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="dee0a-204">Procedures</span></span>  
  
|<span data-ttu-id="dee0a-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="dee0a-205">ColumnName</span></span>|<span data-ttu-id="dee0a-206">DataType</span><span class="sxs-lookup"><span data-stu-id="dee0a-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dee0a-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="dee0a-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="dee0a-208">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-208">String</span></span>|  
|<span data-ttu-id="dee0a-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="dee0a-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="dee0a-210">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-210">String</span></span>|  
|<span data-ttu-id="dee0a-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="dee0a-212">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-212">String</span></span>|  
|<span data-ttu-id="dee0a-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="dee0a-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="dee0a-214">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-214">Int32</span></span>|  
|<span data-ttu-id="dee0a-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="dee0a-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="dee0a-216">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-216">Int32</span></span>|  
|<span data-ttu-id="dee0a-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="dee0a-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="dee0a-218">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-218">Int32</span></span>|  
|<span data-ttu-id="dee0a-219">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="dee0a-219">REMARKS</span></span>|<span data-ttu-id="dee0a-220">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-220">String</span></span>|  
|<span data-ttu-id="dee0a-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="dee0a-222">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="dee0a-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="dee0a-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="dee0a-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="dee0a-224">ColumnName</span></span>|<span data-ttu-id="dee0a-225">DataType</span><span class="sxs-lookup"><span data-stu-id="dee0a-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dee0a-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="dee0a-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="dee0a-227">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-227">String</span></span>|  
|<span data-ttu-id="dee0a-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="dee0a-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="dee0a-229">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-229">String</span></span>|  
|<span data-ttu-id="dee0a-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="dee0a-231">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-231">String</span></span>|  
|<span data-ttu-id="dee0a-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-232">COLUMN_NAME</span></span>|<span data-ttu-id="dee0a-233">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-233">String</span></span>|  
|<span data-ttu-id="dee0a-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-234">COLUMN_TYPE</span></span>|<span data-ttu-id="dee0a-235">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-235">Int16</span></span>|  
|<span data-ttu-id="dee0a-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-236">DATA_TYPE</span></span>|<span data-ttu-id="dee0a-237">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-237">Int16</span></span>|  
|<span data-ttu-id="dee0a-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-238">TYPE_NAME</span></span>|<span data-ttu-id="dee0a-239">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-239">String</span></span>|  
|<span data-ttu-id="dee0a-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="dee0a-240">COLUMN_SIZE</span></span>|<span data-ttu-id="dee0a-241">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-241">Int32</span></span>|  
|<span data-ttu-id="dee0a-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dee0a-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="dee0a-243">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-243">Int32</span></span>|  
|<span data-ttu-id="dee0a-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="dee0a-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="dee0a-245">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-245">Int16</span></span>|  
|<span data-ttu-id="dee0a-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="dee0a-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="dee0a-247">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-247">Int16</span></span>|  
|<span data-ttu-id="dee0a-248">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="dee0a-248">NULLABLE</span></span>|<span data-ttu-id="dee0a-249">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-249">Int16</span></span>|  
|<span data-ttu-id="dee0a-250">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="dee0a-250">REMARKS</span></span>|<span data-ttu-id="dee0a-251">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-251">String</span></span>|  
|<span data-ttu-id="dee0a-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="dee0a-252">COLUMN_DEF</span></span>|<span data-ttu-id="dee0a-253">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-253">String</span></span>|  
|<span data-ttu-id="dee0a-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="dee0a-255">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-255">Int16</span></span>|  
|<span data-ttu-id="dee0a-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="dee0a-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="dee0a-257">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-257">Int16</span></span>|  
|<span data-ttu-id="dee0a-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dee0a-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="dee0a-259">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-259">Int32</span></span>|  
|<span data-ttu-id="dee0a-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dee0a-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="dee0a-261">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-261">Int32</span></span>|  
|<span data-ttu-id="dee0a-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="dee0a-262">IS_NULLABLE</span></span>|<span data-ttu-id="dee0a-263">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-263">String</span></span>|  
|<span data-ttu-id="dee0a-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dee0a-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="dee0a-265">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-265">String</span></span>|  
|<span data-ttu-id="dee0a-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dee0a-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="dee0a-267">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-267">String</span></span>|  
|<span data-ttu-id="dee0a-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="dee0a-269">Byte</span><span class="sxs-lookup"><span data-stu-id="dee0a-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="dee0a-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="dee0a-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="dee0a-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="dee0a-271">ColumnName</span></span>|<span data-ttu-id="dee0a-272">DataType</span><span class="sxs-lookup"><span data-stu-id="dee0a-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dee0a-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="dee0a-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="dee0a-274">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-274">String</span></span>|  
|<span data-ttu-id="dee0a-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="dee0a-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="dee0a-276">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-276">String</span></span>|  
|<span data-ttu-id="dee0a-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="dee0a-278">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-278">String</span></span>|  
|<span data-ttu-id="dee0a-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-279">COLUMN_NAME</span></span>|<span data-ttu-id="dee0a-280">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-280">String</span></span>|  
|<span data-ttu-id="dee0a-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-281">COLUMN_TYPE</span></span>|<span data-ttu-id="dee0a-282">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-282">Int16</span></span>|  
|<span data-ttu-id="dee0a-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-283">DATA_TYPE</span></span>|<span data-ttu-id="dee0a-284">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-284">Int16</span></span>|  
|<span data-ttu-id="dee0a-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-285">TYPE_NAME</span></span>|<span data-ttu-id="dee0a-286">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-286">String</span></span>|  
|<span data-ttu-id="dee0a-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="dee0a-287">COLUMN_SIZE</span></span>|<span data-ttu-id="dee0a-288">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-288">Int32</span></span>|  
|<span data-ttu-id="dee0a-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dee0a-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="dee0a-290">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-290">Int32</span></span>|  
|<span data-ttu-id="dee0a-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="dee0a-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="dee0a-292">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-292">Int16</span></span>|  
|<span data-ttu-id="dee0a-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="dee0a-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="dee0a-294">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-294">Int16</span></span>|  
|<span data-ttu-id="dee0a-295">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="dee0a-295">NULLABLE</span></span>|<span data-ttu-id="dee0a-296">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-296">Int16</span></span>|  
|<span data-ttu-id="dee0a-297">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="dee0a-297">REMARKS</span></span>|<span data-ttu-id="dee0a-298">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-298">String</span></span>|  
|<span data-ttu-id="dee0a-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="dee0a-299">COLUMN_DEF</span></span>|<span data-ttu-id="dee0a-300">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-300">String</span></span>|  
|<span data-ttu-id="dee0a-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="dee0a-302">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-302">Int16</span></span>|  
|<span data-ttu-id="dee0a-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="dee0a-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="dee0a-304">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-304">Int16</span></span>|  
|<span data-ttu-id="dee0a-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dee0a-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="dee0a-306">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-306">Int32</span></span>|  
|<span data-ttu-id="dee0a-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dee0a-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="dee0a-308">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-308">Int32</span></span>|  
|<span data-ttu-id="dee0a-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="dee0a-309">IS_NULLABLE</span></span>|<span data-ttu-id="dee0a-310">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-310">String</span></span>|  
|<span data-ttu-id="dee0a-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dee0a-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="dee0a-312">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-312">String</span></span>|  
|<span data-ttu-id="dee0a-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dee0a-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="dee0a-314">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-314">String</span></span>|  
|<span data-ttu-id="dee0a-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="dee0a-316">Byte</span><span class="sxs-lookup"><span data-stu-id="dee0a-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="dee0a-317">Driver ODBC do Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="dee0a-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="dee0a-318">O Driver ODBC do Microsoft SQL Server Oracle suporta as seguintes coleções de esquema específico, além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="dee0a-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="dee0a-319">Tabelas</span><span class="sxs-lookup"><span data-stu-id="dee0a-319">Tables</span></span>  
  
-   <span data-ttu-id="dee0a-320">Colunas</span><span class="sxs-lookup"><span data-stu-id="dee0a-320">Columns</span></span>  
  
-   <span data-ttu-id="dee0a-321">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="dee0a-321">Procedures</span></span>  
  
-   <span data-ttu-id="dee0a-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="dee0a-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="dee0a-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="dee0a-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="dee0a-324">Exibições</span><span class="sxs-lookup"><span data-stu-id="dee0a-324">Views</span></span>  
  
-   <span data-ttu-id="dee0a-325">Índices</span><span class="sxs-lookup"><span data-stu-id="dee0a-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="dee0a-326">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="dee0a-326">Tables and Views</span></span>  
  
|<span data-ttu-id="dee0a-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="dee0a-327">ColumnName</span></span>|<span data-ttu-id="dee0a-328">DataType</span><span class="sxs-lookup"><span data-stu-id="dee0a-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dee0a-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="dee0a-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="dee0a-330">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-330">String</span></span>|  
|<span data-ttu-id="dee0a-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="dee0a-331">TABLE_OWNER</span></span>|<span data-ttu-id="dee0a-332">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-332">String</span></span>|  
|<span data-ttu-id="dee0a-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-333">TABLE_NAME</span></span>|<span data-ttu-id="dee0a-334">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-334">String</span></span>|  
|<span data-ttu-id="dee0a-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-335">TABLE_TYPE</span></span>|<span data-ttu-id="dee0a-336">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-336">String</span></span>|  
|<span data-ttu-id="dee0a-337">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="dee0a-337">REMARKS</span></span>|<span data-ttu-id="dee0a-338">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="dee0a-339">Colunas</span><span class="sxs-lookup"><span data-stu-id="dee0a-339">Columns</span></span>  
  
|<span data-ttu-id="dee0a-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="dee0a-340">ColumnName</span></span>|<span data-ttu-id="dee0a-341">DataType</span><span class="sxs-lookup"><span data-stu-id="dee0a-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dee0a-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="dee0a-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="dee0a-343">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-343">String</span></span>|  
|<span data-ttu-id="dee0a-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="dee0a-344">TABLE_OWNER</span></span>|<span data-ttu-id="dee0a-345">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-345">String</span></span>|  
|<span data-ttu-id="dee0a-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-346">TABLE_NAME</span></span>|<span data-ttu-id="dee0a-347">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-347">String</span></span>|  
|<span data-ttu-id="dee0a-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-348">COLUMN_NAME</span></span>|<span data-ttu-id="dee0a-349">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-349">String</span></span>|  
|<span data-ttu-id="dee0a-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-350">DATA_TYPE</span></span>|<span data-ttu-id="dee0a-351">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-351">Int16</span></span>|  
|<span data-ttu-id="dee0a-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-352">TYPE_NAME</span></span>|<span data-ttu-id="dee0a-353">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-353">String</span></span>|  
|<span data-ttu-id="dee0a-354">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="dee0a-354">PRECISION</span></span>|<span data-ttu-id="dee0a-355">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-355">Int32</span></span>|  
|<span data-ttu-id="dee0a-356">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="dee0a-356">LENGTH</span></span>|<span data-ttu-id="dee0a-357">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-357">Int32</span></span>|  
|<span data-ttu-id="dee0a-358">ESCALA</span><span class="sxs-lookup"><span data-stu-id="dee0a-358">SCALE</span></span>|<span data-ttu-id="dee0a-359">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-359">Int16</span></span>|  
|<span data-ttu-id="dee0a-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="dee0a-360">RADIX</span></span>|<span data-ttu-id="dee0a-361">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-361">Int16</span></span>|  
|<span data-ttu-id="dee0a-362">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="dee0a-362">NULLABLE</span></span>|<span data-ttu-id="dee0a-363">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-363">Int16</span></span>|  
|<span data-ttu-id="dee0a-364">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="dee0a-364">REMARKS</span></span>|<span data-ttu-id="dee0a-365">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-365">String</span></span>|  
|<span data-ttu-id="dee0a-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dee0a-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="dee0a-367">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="dee0a-368">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="dee0a-368">Procedures</span></span>  
  
|<span data-ttu-id="dee0a-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="dee0a-369">ColumnName</span></span>|<span data-ttu-id="dee0a-370">DataType</span><span class="sxs-lookup"><span data-stu-id="dee0a-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dee0a-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="dee0a-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="dee0a-372">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-372">String</span></span>|  
|<span data-ttu-id="dee0a-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="dee0a-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="dee0a-374">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-374">String</span></span>|  
|<span data-ttu-id="dee0a-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="dee0a-376">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-376">String</span></span>|  
|<span data-ttu-id="dee0a-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="dee0a-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="dee0a-378">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-378">Int16</span></span>|  
|<span data-ttu-id="dee0a-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="dee0a-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="dee0a-380">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-380">Int16</span></span>|  
|<span data-ttu-id="dee0a-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="dee0a-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="dee0a-382">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-382">Int16</span></span>|  
|<span data-ttu-id="dee0a-383">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="dee0a-383">REMARKS</span></span>|<span data-ttu-id="dee0a-384">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-384">String</span></span>|  
|<span data-ttu-id="dee0a-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="dee0a-386">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="dee0a-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="dee0a-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="dee0a-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="dee0a-388">ColumnName</span></span>|<span data-ttu-id="dee0a-389">DataType</span><span class="sxs-lookup"><span data-stu-id="dee0a-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dee0a-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="dee0a-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="dee0a-391">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-391">String</span></span>|  
|<span data-ttu-id="dee0a-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="dee0a-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="dee0a-393">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-393">String</span></span>|  
|<span data-ttu-id="dee0a-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="dee0a-395">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-395">String</span></span>|  
|<span data-ttu-id="dee0a-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-396">COLUMN_NAME</span></span>|<span data-ttu-id="dee0a-397">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-397">String</span></span>|  
|<span data-ttu-id="dee0a-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-398">COLUMN_TYPE</span></span>|<span data-ttu-id="dee0a-399">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-399">Int16</span></span>|  
|<span data-ttu-id="dee0a-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-400">DATA_TYPE</span></span>|<span data-ttu-id="dee0a-401">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-401">Int16</span></span>|  
|<span data-ttu-id="dee0a-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-402">TYPE_NAME</span></span>|<span data-ttu-id="dee0a-403">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-403">String</span></span>|  
|<span data-ttu-id="dee0a-404">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="dee0a-404">PRECISION</span></span>|<span data-ttu-id="dee0a-405">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-405">Int32</span></span>|  
|<span data-ttu-id="dee0a-406">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="dee0a-406">LENGTH</span></span>|<span data-ttu-id="dee0a-407">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-407">Int32</span></span>|  
|<span data-ttu-id="dee0a-408">ESCALA</span><span class="sxs-lookup"><span data-stu-id="dee0a-408">SCALE</span></span>|<span data-ttu-id="dee0a-409">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-409">Int16</span></span>|  
|<span data-ttu-id="dee0a-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="dee0a-410">RADIX</span></span>|<span data-ttu-id="dee0a-411">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-411">Int16</span></span>|  
|<span data-ttu-id="dee0a-412">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="dee0a-412">NULLABLE</span></span>|<span data-ttu-id="dee0a-413">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-413">Int16</span></span>|  
|<span data-ttu-id="dee0a-414">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="dee0a-414">REMARKS</span></span>|<span data-ttu-id="dee0a-415">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-415">String</span></span>|  
|<span data-ttu-id="dee0a-416">SOBRECARGA</span><span class="sxs-lookup"><span data-stu-id="dee0a-416">OVERLOAD</span></span>|<span data-ttu-id="dee0a-417">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-417">Int32</span></span>|  
|<span data-ttu-id="dee0a-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dee0a-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="dee0a-419">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="dee0a-420">Microsoft Jet ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="dee0a-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="dee0a-421">O Driver ODBC do Microsoft Jet suporta as seguintes coleções de esquema específico, além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="dee0a-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="dee0a-422">Tabelas</span><span class="sxs-lookup"><span data-stu-id="dee0a-422">Tables</span></span>  
  
-   <span data-ttu-id="dee0a-423">Índices</span><span class="sxs-lookup"><span data-stu-id="dee0a-423">Indexes</span></span>  
  
-   <span data-ttu-id="dee0a-424">Colunas</span><span class="sxs-lookup"><span data-stu-id="dee0a-424">Columns</span></span>  
  
-   <span data-ttu-id="dee0a-425">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="dee0a-425">Procedures</span></span>  
  
-   <span data-ttu-id="dee0a-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="dee0a-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="dee0a-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="dee0a-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="dee0a-428">Exibições</span><span class="sxs-lookup"><span data-stu-id="dee0a-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="dee0a-429">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="dee0a-429">Tables and Views</span></span>  
  
|<span data-ttu-id="dee0a-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="dee0a-430">ColumnName</span></span>|<span data-ttu-id="dee0a-431">DataType</span><span class="sxs-lookup"><span data-stu-id="dee0a-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dee0a-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="dee0a-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="dee0a-433">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-433">String</span></span>|  
|<span data-ttu-id="dee0a-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="dee0a-434">TABLE_OWNER</span></span>|<span data-ttu-id="dee0a-435">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-435">String</span></span>|  
|<span data-ttu-id="dee0a-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-436">TABLE_NAME</span></span>|<span data-ttu-id="dee0a-437">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-437">String</span></span>|  
|<span data-ttu-id="dee0a-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-438">TABLE_TYPE</span></span>|<span data-ttu-id="dee0a-439">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-439">String</span></span>|  
|<span data-ttu-id="dee0a-440">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="dee0a-440">REMARKS</span></span>|<span data-ttu-id="dee0a-441">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="dee0a-442">Colunas</span><span class="sxs-lookup"><span data-stu-id="dee0a-442">Columns</span></span>  
  
|<span data-ttu-id="dee0a-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="dee0a-443">ColumnName</span></span>|<span data-ttu-id="dee0a-444">DataType</span><span class="sxs-lookup"><span data-stu-id="dee0a-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dee0a-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="dee0a-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="dee0a-446">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-446">String</span></span>|  
|<span data-ttu-id="dee0a-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="dee0a-447">TABLE_OWNER</span></span>|<span data-ttu-id="dee0a-448">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-448">String</span></span>|  
|<span data-ttu-id="dee0a-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-449">TABLE_NAME</span></span>|<span data-ttu-id="dee0a-450">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-450">String</span></span>|  
|<span data-ttu-id="dee0a-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-451">COLUMN_NAME</span></span>|<span data-ttu-id="dee0a-452">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-452">String</span></span>|  
|<span data-ttu-id="dee0a-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-453">DATA_TYPE</span></span>|<span data-ttu-id="dee0a-454">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-454">Int16</span></span>|  
|<span data-ttu-id="dee0a-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-455">TYPE_NAME</span></span>|<span data-ttu-id="dee0a-456">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-456">String</span></span>|  
|<span data-ttu-id="dee0a-457">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="dee0a-457">PRECISION</span></span>|<span data-ttu-id="dee0a-458">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-458">Int32</span></span>|  
|<span data-ttu-id="dee0a-459">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="dee0a-459">LENGTH</span></span>|<span data-ttu-id="dee0a-460">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-460">Int32</span></span>|  
|<span data-ttu-id="dee0a-461">ESCALA</span><span class="sxs-lookup"><span data-stu-id="dee0a-461">SCALE</span></span>|<span data-ttu-id="dee0a-462">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-462">Int16</span></span>|  
|<span data-ttu-id="dee0a-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="dee0a-463">RADIX</span></span>|<span data-ttu-id="dee0a-464">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-464">Int16</span></span>|  
|<span data-ttu-id="dee0a-465">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="dee0a-465">NULLABLE</span></span>|<span data-ttu-id="dee0a-466">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-466">Int16</span></span>|  
|<span data-ttu-id="dee0a-467">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="dee0a-467">REMARKS</span></span>|<span data-ttu-id="dee0a-468">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-468">String</span></span>|  
|<span data-ttu-id="dee0a-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dee0a-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="dee0a-470">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="dee0a-471">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="dee0a-471">Procedures</span></span>  
  
|<span data-ttu-id="dee0a-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="dee0a-472">ColumnName</span></span>|<span data-ttu-id="dee0a-473">DataType</span><span class="sxs-lookup"><span data-stu-id="dee0a-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dee0a-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="dee0a-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="dee0a-475">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-475">String</span></span>|  
|<span data-ttu-id="dee0a-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="dee0a-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="dee0a-477">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-477">String</span></span>|  
|<span data-ttu-id="dee0a-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="dee0a-479">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-479">String</span></span>|  
|<span data-ttu-id="dee0a-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="dee0a-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="dee0a-481">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-481">Int16</span></span>|  
|<span data-ttu-id="dee0a-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="dee0a-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="dee0a-483">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-483">Int16</span></span>|  
|<span data-ttu-id="dee0a-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="dee0a-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="dee0a-485">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-485">Int16</span></span>|  
|<span data-ttu-id="dee0a-486">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="dee0a-486">REMARKS</span></span>|<span data-ttu-id="dee0a-487">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-487">String</span></span>|  
|<span data-ttu-id="dee0a-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="dee0a-489">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="dee0a-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="dee0a-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="dee0a-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="dee0a-491">ColumnName</span></span>|<span data-ttu-id="dee0a-492">DataType</span><span class="sxs-lookup"><span data-stu-id="dee0a-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dee0a-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="dee0a-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="dee0a-494">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-494">String</span></span>|  
|<span data-ttu-id="dee0a-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="dee0a-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="dee0a-496">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-496">String</span></span>|  
|<span data-ttu-id="dee0a-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="dee0a-498">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-498">String</span></span>|  
|<span data-ttu-id="dee0a-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-499">COLUMN_NAME</span></span>|<span data-ttu-id="dee0a-500">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-500">String</span></span>|  
|<span data-ttu-id="dee0a-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-501">COLUMN_TYPE</span></span>|<span data-ttu-id="dee0a-502">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-502">Int16</span></span>|  
|<span data-ttu-id="dee0a-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-503">DATA_TYPE</span></span>|<span data-ttu-id="dee0a-504">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-504">Int16</span></span>|  
|<span data-ttu-id="dee0a-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-505">TYPE_NAME</span></span>|<span data-ttu-id="dee0a-506">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-506">String</span></span>|  
|<span data-ttu-id="dee0a-507">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="dee0a-507">PRECISION</span></span>|<span data-ttu-id="dee0a-508">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-508">Int32</span></span>|  
|<span data-ttu-id="dee0a-509">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="dee0a-509">LENGTH</span></span>|<span data-ttu-id="dee0a-510">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-510">Int32</span></span>|  
|<span data-ttu-id="dee0a-511">ESCALA</span><span class="sxs-lookup"><span data-stu-id="dee0a-511">SCALE</span></span>|<span data-ttu-id="dee0a-512">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-512">Int16</span></span>|  
|<span data-ttu-id="dee0a-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="dee0a-513">RADIX</span></span>|<span data-ttu-id="dee0a-514">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-514">Int16</span></span>|  
|<span data-ttu-id="dee0a-515">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="dee0a-515">NULLABLE</span></span>|<span data-ttu-id="dee0a-516">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-516">Int16</span></span>|  
|<span data-ttu-id="dee0a-517">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="dee0a-517">REMARKS</span></span>|<span data-ttu-id="dee0a-518">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-518">String</span></span>|  
|<span data-ttu-id="dee0a-519">SOBRECARGA</span><span class="sxs-lookup"><span data-stu-id="dee0a-519">OVERLOAD</span></span>|<span data-ttu-id="dee0a-520">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-520">Int32</span></span>|  
|<span data-ttu-id="dee0a-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dee0a-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="dee0a-522">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="dee0a-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="dee0a-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="dee0a-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="dee0a-524">ColumnName</span></span>|<span data-ttu-id="dee0a-525">DataType</span><span class="sxs-lookup"><span data-stu-id="dee0a-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="dee0a-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="dee0a-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="dee0a-527">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-527">String</span></span>|  
|<span data-ttu-id="dee0a-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="dee0a-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="dee0a-529">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-529">String</span></span>|  
|<span data-ttu-id="dee0a-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="dee0a-531">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-531">String</span></span>|  
|<span data-ttu-id="dee0a-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-532">COLUMN_NAME</span></span>|<span data-ttu-id="dee0a-533">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-533">String</span></span>|  
|<span data-ttu-id="dee0a-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-534">COLUMN_TYPE</span></span>|<span data-ttu-id="dee0a-535">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-535">Int16</span></span>|  
|<span data-ttu-id="dee0a-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-536">DATA_TYPE</span></span>|<span data-ttu-id="dee0a-537">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-537">Int16</span></span>|  
|<span data-ttu-id="dee0a-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="dee0a-538">TYPE_NAME</span></span>|<span data-ttu-id="dee0a-539">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-539">String</span></span>|  
|<span data-ttu-id="dee0a-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="dee0a-540">COLUMN_SIZE</span></span>|<span data-ttu-id="dee0a-541">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-541">Int32</span></span>|  
|<span data-ttu-id="dee0a-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dee0a-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="dee0a-543">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-543">Int32</span></span>|  
|<span data-ttu-id="dee0a-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="dee0a-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="dee0a-545">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-545">Int16</span></span>|  
|<span data-ttu-id="dee0a-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="dee0a-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="dee0a-547">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-547">Int16</span></span>|  
|<span data-ttu-id="dee0a-548">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="dee0a-548">NULLABLE</span></span>|<span data-ttu-id="dee0a-549">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-549">Int16</span></span>|  
|<span data-ttu-id="dee0a-550">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="dee0a-550">REMARKS</span></span>|<span data-ttu-id="dee0a-551">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-551">String</span></span>|  
|<span data-ttu-id="dee0a-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="dee0a-552">COLUMN_DEF</span></span>|<span data-ttu-id="dee0a-553">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-553">String</span></span>|  
|<span data-ttu-id="dee0a-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="dee0a-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="dee0a-555">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-555">Int16</span></span>|  
|<span data-ttu-id="dee0a-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="dee0a-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="dee0a-557">Int16</span><span class="sxs-lookup"><span data-stu-id="dee0a-557">Int16</span></span>|  
|<span data-ttu-id="dee0a-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="dee0a-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="dee0a-559">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-559">Int32</span></span>|  
|<span data-ttu-id="dee0a-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="dee0a-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="dee0a-561">Int32</span><span class="sxs-lookup"><span data-stu-id="dee0a-561">Int32</span></span>|  
|<span data-ttu-id="dee0a-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="dee0a-562">IS_NULLABLE</span></span>|<span data-ttu-id="dee0a-563">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dee0a-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dee0a-564">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dee0a-564">See Also</span></span>  
 <span data-ttu-id="dee0a-565">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="dee0a-565">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
