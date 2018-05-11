---
title: Coleções de esquema ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: 36d0859b897bfcea33803c219ade14722ed90421
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="da274-102">Coleções de esquema ODBC</span><span class="sxs-lookup"><span data-stu-id="da274-102">ODBC Schema Collections</span></span>
<span data-ttu-id="da274-103">Esta seção discute o suporte de coleção de esquema para os drivers ODBC para Microsoft SQL Server, Oracle e Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="da274-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="da274-104">Driver ODBC do Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="da274-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="da274-105">O Driver ODBC do Microsoft SQL Server suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="da274-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="da274-106">Tabelas</span><span class="sxs-lookup"><span data-stu-id="da274-106">Tables</span></span>  
  
-   <span data-ttu-id="da274-107">Índices</span><span class="sxs-lookup"><span data-stu-id="da274-107">Indexes</span></span>  
  
-   <span data-ttu-id="da274-108">Colunas</span><span class="sxs-lookup"><span data-stu-id="da274-108">Columns</span></span>  
  
-   <span data-ttu-id="da274-109">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="da274-109">Procedures</span></span>  
  
-   <span data-ttu-id="da274-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="da274-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="da274-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="da274-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="da274-112">Exibições</span><span class="sxs-lookup"><span data-stu-id="da274-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="da274-113">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="da274-113">Tables and Views</span></span>  
  
|<span data-ttu-id="da274-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="da274-114">ColumnName</span></span>|<span data-ttu-id="da274-115">DataType</span><span class="sxs-lookup"><span data-stu-id="da274-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="da274-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="da274-116">TABLE_CAT</span></span>|<span data-ttu-id="da274-117">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-117">String</span></span>|  
|<span data-ttu-id="da274-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="da274-118">TABLE_SCHEM</span></span>|<span data-ttu-id="da274-119">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-119">String</span></span>|  
|<span data-ttu-id="da274-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-120">TABLE_NAME</span></span>|<span data-ttu-id="da274-121">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-121">String</span></span>|  
|<span data-ttu-id="da274-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-122">TABLE_TYPE</span></span>|<span data-ttu-id="da274-123">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-123">String</span></span>|  
|<span data-ttu-id="da274-124">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="da274-124">REMARKS</span></span>|<span data-ttu-id="da274-125">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="da274-126">Índices</span><span class="sxs-lookup"><span data-stu-id="da274-126">Indexes</span></span>  
  
|<span data-ttu-id="da274-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="da274-127">ColumnName</span></span>|<span data-ttu-id="da274-128">DataType</span><span class="sxs-lookup"><span data-stu-id="da274-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="da274-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="da274-129">TABLE_CAT</span></span>|<span data-ttu-id="da274-130">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-130">String</span></span>|  
|<span data-ttu-id="da274-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="da274-131">TABLE_SCHEM</span></span>|<span data-ttu-id="da274-132">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-132">String</span></span>|  
|<span data-ttu-id="da274-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-133">TABLE_NAME</span></span>|<span data-ttu-id="da274-134">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-134">String</span></span>|  
|<span data-ttu-id="da274-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="da274-135">NON_UNIQUE</span></span>|<span data-ttu-id="da274-136">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-136">Int16</span></span>|  
|<span data-ttu-id="da274-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="da274-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="da274-138">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-138">String</span></span>|  
|<span data-ttu-id="da274-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-139">INDEX_NAME</span></span>|<span data-ttu-id="da274-140">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-140">String</span></span>|  
|<span data-ttu-id="da274-141">TIPO DE</span><span class="sxs-lookup"><span data-stu-id="da274-141">TYPE</span></span>|<span data-ttu-id="da274-142">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-142">Int16</span></span>|  
|<span data-ttu-id="da274-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="da274-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="da274-144">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-144">Int16</span></span>|  
|<span data-ttu-id="da274-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-145">COLUMN_NAME</span></span>|<span data-ttu-id="da274-146">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-146">String</span></span>|  
|<span data-ttu-id="da274-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="da274-147">ASC_OR_DESC</span></span>|<span data-ttu-id="da274-148">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-148">String</span></span>|  
|<span data-ttu-id="da274-149">CARDINALIDADE</span><span class="sxs-lookup"><span data-stu-id="da274-149">CARDINATLITY</span></span>|<span data-ttu-id="da274-150">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-150">Int32</span></span>|  
|<span data-ttu-id="da274-151">PÁGINAS</span><span class="sxs-lookup"><span data-stu-id="da274-151">PAGES</span></span>|<span data-ttu-id="da274-152">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-152">Int32</span></span>|  
|<span data-ttu-id="da274-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="da274-153">FILTER_CONDITION</span></span>|<span data-ttu-id="da274-154">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-154">String</span></span>|  
|<span data-ttu-id="da274-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="da274-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="da274-156">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-156">String</span></span>|  
|<span data-ttu-id="da274-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="da274-158">Byte</span><span class="sxs-lookup"><span data-stu-id="da274-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="da274-159">Colunas</span><span class="sxs-lookup"><span data-stu-id="da274-159">Columns</span></span>  
  
|<span data-ttu-id="da274-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="da274-160">ColumnName</span></span>|<span data-ttu-id="da274-161">DataType</span><span class="sxs-lookup"><span data-stu-id="da274-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="da274-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="da274-162">TABLE_CAT</span></span>|<span data-ttu-id="da274-163">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-163">String</span></span>|  
|<span data-ttu-id="da274-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="da274-164">TABLE_SCHEM</span></span>|<span data-ttu-id="da274-165">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-165">String</span></span>|  
|<span data-ttu-id="da274-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-166">TABLE_NAME</span></span>|<span data-ttu-id="da274-167">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-167">String</span></span>|  
|<span data-ttu-id="da274-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-168">COLUMN_NAME</span></span>|<span data-ttu-id="da274-169">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-169">String</span></span>|  
|<span data-ttu-id="da274-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-170">DATA_TYPE</span></span>|<span data-ttu-id="da274-171">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-171">Int16</span></span>|  
|<span data-ttu-id="da274-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-172">TYPE_NAME</span></span>|<span data-ttu-id="da274-173">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-173">String</span></span>|  
|<span data-ttu-id="da274-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="da274-174">COLUMN_SIZE</span></span>|<span data-ttu-id="da274-175">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-175">Int32</span></span>|  
|<span data-ttu-id="da274-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="da274-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="da274-177">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-177">Int32</span></span>|  
|<span data-ttu-id="da274-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="da274-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="da274-179">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-179">Int16</span></span>|  
|<span data-ttu-id="da274-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="da274-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="da274-181">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-181">Int16</span></span>|  
|<span data-ttu-id="da274-182">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="da274-182">NULLABLE</span></span>|<span data-ttu-id="da274-183">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-183">Int16</span></span>|  
|<span data-ttu-id="da274-184">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="da274-184">REMARKS</span></span>|<span data-ttu-id="da274-185">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-185">String</span></span>|  
|<span data-ttu-id="da274-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="da274-186">COLUMN_DEF</span></span>|<span data-ttu-id="da274-187">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-187">String</span></span>|  
|<span data-ttu-id="da274-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="da274-189">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-189">Int16</span></span>|  
|<span data-ttu-id="da274-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="da274-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="da274-191">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-191">Int16</span></span>|  
|<span data-ttu-id="da274-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="da274-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="da274-193">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-193">Int32</span></span>|  
|<span data-ttu-id="da274-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="da274-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="da274-195">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-195">Int32</span></span>|  
|<span data-ttu-id="da274-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="da274-196">IS_NULLABLE</span></span>|<span data-ttu-id="da274-197">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-197">String</span></span>|  
|<span data-ttu-id="da274-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="da274-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="da274-199">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-199">String</span></span>|  
|<span data-ttu-id="da274-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="da274-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="da274-201">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-201">String</span></span>|  
|<span data-ttu-id="da274-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="da274-203">Byte</span><span class="sxs-lookup"><span data-stu-id="da274-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="da274-204">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="da274-204">Procedures</span></span>  
  
|<span data-ttu-id="da274-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="da274-205">ColumnName</span></span>|<span data-ttu-id="da274-206">DataType</span><span class="sxs-lookup"><span data-stu-id="da274-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="da274-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="da274-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="da274-208">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-208">String</span></span>|  
|<span data-ttu-id="da274-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="da274-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="da274-210">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-210">String</span></span>|  
|<span data-ttu-id="da274-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="da274-212">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-212">String</span></span>|  
|<span data-ttu-id="da274-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="da274-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="da274-214">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-214">Int32</span></span>|  
|<span data-ttu-id="da274-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="da274-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="da274-216">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-216">Int32</span></span>|  
|<span data-ttu-id="da274-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="da274-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="da274-218">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-218">Int32</span></span>|  
|<span data-ttu-id="da274-219">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="da274-219">REMARKS</span></span>|<span data-ttu-id="da274-220">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-220">String</span></span>|  
|<span data-ttu-id="da274-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="da274-222">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="da274-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="da274-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="da274-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="da274-224">ColumnName</span></span>|<span data-ttu-id="da274-225">DataType</span><span class="sxs-lookup"><span data-stu-id="da274-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="da274-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="da274-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="da274-227">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-227">String</span></span>|  
|<span data-ttu-id="da274-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="da274-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="da274-229">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-229">String</span></span>|  
|<span data-ttu-id="da274-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="da274-231">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-231">String</span></span>|  
|<span data-ttu-id="da274-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-232">COLUMN_NAME</span></span>|<span data-ttu-id="da274-233">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-233">String</span></span>|  
|<span data-ttu-id="da274-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-234">COLUMN_TYPE</span></span>|<span data-ttu-id="da274-235">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-235">Int16</span></span>|  
|<span data-ttu-id="da274-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-236">DATA_TYPE</span></span>|<span data-ttu-id="da274-237">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-237">Int16</span></span>|  
|<span data-ttu-id="da274-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-238">TYPE_NAME</span></span>|<span data-ttu-id="da274-239">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-239">String</span></span>|  
|<span data-ttu-id="da274-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="da274-240">COLUMN_SIZE</span></span>|<span data-ttu-id="da274-241">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-241">Int32</span></span>|  
|<span data-ttu-id="da274-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="da274-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="da274-243">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-243">Int32</span></span>|  
|<span data-ttu-id="da274-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="da274-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="da274-245">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-245">Int16</span></span>|  
|<span data-ttu-id="da274-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="da274-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="da274-247">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-247">Int16</span></span>|  
|<span data-ttu-id="da274-248">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="da274-248">NULLABLE</span></span>|<span data-ttu-id="da274-249">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-249">Int16</span></span>|  
|<span data-ttu-id="da274-250">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="da274-250">REMARKS</span></span>|<span data-ttu-id="da274-251">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-251">String</span></span>|  
|<span data-ttu-id="da274-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="da274-252">COLUMN_DEF</span></span>|<span data-ttu-id="da274-253">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-253">String</span></span>|  
|<span data-ttu-id="da274-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="da274-255">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-255">Int16</span></span>|  
|<span data-ttu-id="da274-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="da274-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="da274-257">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-257">Int16</span></span>|  
|<span data-ttu-id="da274-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="da274-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="da274-259">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-259">Int32</span></span>|  
|<span data-ttu-id="da274-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="da274-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="da274-261">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-261">Int32</span></span>|  
|<span data-ttu-id="da274-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="da274-262">IS_NULLABLE</span></span>|<span data-ttu-id="da274-263">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-263">String</span></span>|  
|<span data-ttu-id="da274-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="da274-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="da274-265">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-265">String</span></span>|  
|<span data-ttu-id="da274-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="da274-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="da274-267">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-267">String</span></span>|  
|<span data-ttu-id="da274-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="da274-269">Byte</span><span class="sxs-lookup"><span data-stu-id="da274-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="da274-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="da274-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="da274-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="da274-271">ColumnName</span></span>|<span data-ttu-id="da274-272">DataType</span><span class="sxs-lookup"><span data-stu-id="da274-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="da274-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="da274-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="da274-274">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-274">String</span></span>|  
|<span data-ttu-id="da274-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="da274-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="da274-276">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-276">String</span></span>|  
|<span data-ttu-id="da274-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="da274-278">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-278">String</span></span>|  
|<span data-ttu-id="da274-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-279">COLUMN_NAME</span></span>|<span data-ttu-id="da274-280">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-280">String</span></span>|  
|<span data-ttu-id="da274-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-281">COLUMN_TYPE</span></span>|<span data-ttu-id="da274-282">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-282">Int16</span></span>|  
|<span data-ttu-id="da274-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-283">DATA_TYPE</span></span>|<span data-ttu-id="da274-284">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-284">Int16</span></span>|  
|<span data-ttu-id="da274-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-285">TYPE_NAME</span></span>|<span data-ttu-id="da274-286">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-286">String</span></span>|  
|<span data-ttu-id="da274-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="da274-287">COLUMN_SIZE</span></span>|<span data-ttu-id="da274-288">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-288">Int32</span></span>|  
|<span data-ttu-id="da274-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="da274-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="da274-290">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-290">Int32</span></span>|  
|<span data-ttu-id="da274-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="da274-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="da274-292">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-292">Int16</span></span>|  
|<span data-ttu-id="da274-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="da274-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="da274-294">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-294">Int16</span></span>|  
|<span data-ttu-id="da274-295">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="da274-295">NULLABLE</span></span>|<span data-ttu-id="da274-296">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-296">Int16</span></span>|  
|<span data-ttu-id="da274-297">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="da274-297">REMARKS</span></span>|<span data-ttu-id="da274-298">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-298">String</span></span>|  
|<span data-ttu-id="da274-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="da274-299">COLUMN_DEF</span></span>|<span data-ttu-id="da274-300">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-300">String</span></span>|  
|<span data-ttu-id="da274-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="da274-302">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-302">Int16</span></span>|  
|<span data-ttu-id="da274-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="da274-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="da274-304">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-304">Int16</span></span>|  
|<span data-ttu-id="da274-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="da274-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="da274-306">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-306">Int32</span></span>|  
|<span data-ttu-id="da274-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="da274-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="da274-308">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-308">Int32</span></span>|  
|<span data-ttu-id="da274-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="da274-309">IS_NULLABLE</span></span>|<span data-ttu-id="da274-310">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-310">String</span></span>|  
|<span data-ttu-id="da274-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="da274-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="da274-312">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-312">String</span></span>|  
|<span data-ttu-id="da274-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="da274-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="da274-314">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-314">String</span></span>|  
|<span data-ttu-id="da274-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="da274-316">Byte</span><span class="sxs-lookup"><span data-stu-id="da274-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="da274-317">Driver ODBC do Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="da274-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="da274-318">O Driver ODBC do Microsoft SQL Server Oracle suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="da274-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="da274-319">Tabelas</span><span class="sxs-lookup"><span data-stu-id="da274-319">Tables</span></span>  
  
-   <span data-ttu-id="da274-320">Colunas</span><span class="sxs-lookup"><span data-stu-id="da274-320">Columns</span></span>  
  
-   <span data-ttu-id="da274-321">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="da274-321">Procedures</span></span>  
  
-   <span data-ttu-id="da274-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="da274-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="da274-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="da274-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="da274-324">Exibições</span><span class="sxs-lookup"><span data-stu-id="da274-324">Views</span></span>  
  
-   <span data-ttu-id="da274-325">Índices</span><span class="sxs-lookup"><span data-stu-id="da274-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="da274-326">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="da274-326">Tables and Views</span></span>  
  
|<span data-ttu-id="da274-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="da274-327">ColumnName</span></span>|<span data-ttu-id="da274-328">DataType</span><span class="sxs-lookup"><span data-stu-id="da274-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="da274-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="da274-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="da274-330">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-330">String</span></span>|  
|<span data-ttu-id="da274-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="da274-331">TABLE_OWNER</span></span>|<span data-ttu-id="da274-332">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-332">String</span></span>|  
|<span data-ttu-id="da274-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-333">TABLE_NAME</span></span>|<span data-ttu-id="da274-334">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-334">String</span></span>|  
|<span data-ttu-id="da274-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-335">TABLE_TYPE</span></span>|<span data-ttu-id="da274-336">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-336">String</span></span>|  
|<span data-ttu-id="da274-337">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="da274-337">REMARKS</span></span>|<span data-ttu-id="da274-338">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="da274-339">Colunas</span><span class="sxs-lookup"><span data-stu-id="da274-339">Columns</span></span>  
  
|<span data-ttu-id="da274-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="da274-340">ColumnName</span></span>|<span data-ttu-id="da274-341">DataType</span><span class="sxs-lookup"><span data-stu-id="da274-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="da274-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="da274-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="da274-343">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-343">String</span></span>|  
|<span data-ttu-id="da274-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="da274-344">TABLE_OWNER</span></span>|<span data-ttu-id="da274-345">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-345">String</span></span>|  
|<span data-ttu-id="da274-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-346">TABLE_NAME</span></span>|<span data-ttu-id="da274-347">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-347">String</span></span>|  
|<span data-ttu-id="da274-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-348">COLUMN_NAME</span></span>|<span data-ttu-id="da274-349">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-349">String</span></span>|  
|<span data-ttu-id="da274-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-350">DATA_TYPE</span></span>|<span data-ttu-id="da274-351">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-351">Int16</span></span>|  
|<span data-ttu-id="da274-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-352">TYPE_NAME</span></span>|<span data-ttu-id="da274-353">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-353">String</span></span>|  
|<span data-ttu-id="da274-354">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="da274-354">PRECISION</span></span>|<span data-ttu-id="da274-355">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-355">Int32</span></span>|  
|<span data-ttu-id="da274-356">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="da274-356">LENGTH</span></span>|<span data-ttu-id="da274-357">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-357">Int32</span></span>|  
|<span data-ttu-id="da274-358">ESCALA</span><span class="sxs-lookup"><span data-stu-id="da274-358">SCALE</span></span>|<span data-ttu-id="da274-359">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-359">Int16</span></span>|  
|<span data-ttu-id="da274-360">BASE</span><span class="sxs-lookup"><span data-stu-id="da274-360">RADIX</span></span>|<span data-ttu-id="da274-361">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-361">Int16</span></span>|  
|<span data-ttu-id="da274-362">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="da274-362">NULLABLE</span></span>|<span data-ttu-id="da274-363">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-363">Int16</span></span>|  
|<span data-ttu-id="da274-364">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="da274-364">REMARKS</span></span>|<span data-ttu-id="da274-365">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-365">String</span></span>|  
|<span data-ttu-id="da274-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="da274-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="da274-367">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="da274-368">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="da274-368">Procedures</span></span>  
  
|<span data-ttu-id="da274-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="da274-369">ColumnName</span></span>|<span data-ttu-id="da274-370">DataType</span><span class="sxs-lookup"><span data-stu-id="da274-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="da274-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="da274-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="da274-372">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-372">String</span></span>|  
|<span data-ttu-id="da274-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="da274-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="da274-374">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-374">String</span></span>|  
|<span data-ttu-id="da274-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="da274-376">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-376">String</span></span>|  
|<span data-ttu-id="da274-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="da274-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="da274-378">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-378">Int16</span></span>|  
|<span data-ttu-id="da274-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="da274-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="da274-380">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-380">Int16</span></span>|  
|<span data-ttu-id="da274-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="da274-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="da274-382">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-382">Int16</span></span>|  
|<span data-ttu-id="da274-383">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="da274-383">REMARKS</span></span>|<span data-ttu-id="da274-384">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-384">String</span></span>|  
|<span data-ttu-id="da274-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="da274-386">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="da274-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="da274-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="da274-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="da274-388">ColumnName</span></span>|<span data-ttu-id="da274-389">DataType</span><span class="sxs-lookup"><span data-stu-id="da274-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="da274-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="da274-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="da274-391">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-391">String</span></span>|  
|<span data-ttu-id="da274-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="da274-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="da274-393">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-393">String</span></span>|  
|<span data-ttu-id="da274-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="da274-395">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-395">String</span></span>|  
|<span data-ttu-id="da274-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-396">COLUMN_NAME</span></span>|<span data-ttu-id="da274-397">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-397">String</span></span>|  
|<span data-ttu-id="da274-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-398">COLUMN_TYPE</span></span>|<span data-ttu-id="da274-399">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-399">Int16</span></span>|  
|<span data-ttu-id="da274-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-400">DATA_TYPE</span></span>|<span data-ttu-id="da274-401">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-401">Int16</span></span>|  
|<span data-ttu-id="da274-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-402">TYPE_NAME</span></span>|<span data-ttu-id="da274-403">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-403">String</span></span>|  
|<span data-ttu-id="da274-404">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="da274-404">PRECISION</span></span>|<span data-ttu-id="da274-405">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-405">Int32</span></span>|  
|<span data-ttu-id="da274-406">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="da274-406">LENGTH</span></span>|<span data-ttu-id="da274-407">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-407">Int32</span></span>|  
|<span data-ttu-id="da274-408">ESCALA</span><span class="sxs-lookup"><span data-stu-id="da274-408">SCALE</span></span>|<span data-ttu-id="da274-409">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-409">Int16</span></span>|  
|<span data-ttu-id="da274-410">BASE</span><span class="sxs-lookup"><span data-stu-id="da274-410">RADIX</span></span>|<span data-ttu-id="da274-411">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-411">Int16</span></span>|  
|<span data-ttu-id="da274-412">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="da274-412">NULLABLE</span></span>|<span data-ttu-id="da274-413">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-413">Int16</span></span>|  
|<span data-ttu-id="da274-414">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="da274-414">REMARKS</span></span>|<span data-ttu-id="da274-415">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-415">String</span></span>|  
|<span data-ttu-id="da274-416">SOBRECARGA</span><span class="sxs-lookup"><span data-stu-id="da274-416">OVERLOAD</span></span>|<span data-ttu-id="da274-417">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-417">Int32</span></span>|  
|<span data-ttu-id="da274-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="da274-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="da274-419">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="da274-420">Microsoft Jet ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="da274-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="da274-421">O Driver de ODBC do Microsoft Jet suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="da274-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="da274-422">Tabelas</span><span class="sxs-lookup"><span data-stu-id="da274-422">Tables</span></span>  
  
-   <span data-ttu-id="da274-423">Índices</span><span class="sxs-lookup"><span data-stu-id="da274-423">Indexes</span></span>  
  
-   <span data-ttu-id="da274-424">Colunas</span><span class="sxs-lookup"><span data-stu-id="da274-424">Columns</span></span>  
  
-   <span data-ttu-id="da274-425">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="da274-425">Procedures</span></span>  
  
-   <span data-ttu-id="da274-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="da274-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="da274-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="da274-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="da274-428">Exibições</span><span class="sxs-lookup"><span data-stu-id="da274-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="da274-429">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="da274-429">Tables and Views</span></span>  
  
|<span data-ttu-id="da274-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="da274-430">ColumnName</span></span>|<span data-ttu-id="da274-431">DataType</span><span class="sxs-lookup"><span data-stu-id="da274-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="da274-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="da274-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="da274-433">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-433">String</span></span>|  
|<span data-ttu-id="da274-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="da274-434">TABLE_OWNER</span></span>|<span data-ttu-id="da274-435">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-435">String</span></span>|  
|<span data-ttu-id="da274-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-436">TABLE_NAME</span></span>|<span data-ttu-id="da274-437">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-437">String</span></span>|  
|<span data-ttu-id="da274-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-438">TABLE_TYPE</span></span>|<span data-ttu-id="da274-439">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-439">String</span></span>|  
|<span data-ttu-id="da274-440">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="da274-440">REMARKS</span></span>|<span data-ttu-id="da274-441">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="da274-442">Colunas</span><span class="sxs-lookup"><span data-stu-id="da274-442">Columns</span></span>  
  
|<span data-ttu-id="da274-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="da274-443">ColumnName</span></span>|<span data-ttu-id="da274-444">DataType</span><span class="sxs-lookup"><span data-stu-id="da274-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="da274-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="da274-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="da274-446">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-446">String</span></span>|  
|<span data-ttu-id="da274-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="da274-447">TABLE_OWNER</span></span>|<span data-ttu-id="da274-448">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-448">String</span></span>|  
|<span data-ttu-id="da274-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-449">TABLE_NAME</span></span>|<span data-ttu-id="da274-450">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-450">String</span></span>|  
|<span data-ttu-id="da274-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-451">COLUMN_NAME</span></span>|<span data-ttu-id="da274-452">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-452">String</span></span>|  
|<span data-ttu-id="da274-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-453">DATA_TYPE</span></span>|<span data-ttu-id="da274-454">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-454">Int16</span></span>|  
|<span data-ttu-id="da274-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-455">TYPE_NAME</span></span>|<span data-ttu-id="da274-456">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-456">String</span></span>|  
|<span data-ttu-id="da274-457">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="da274-457">PRECISION</span></span>|<span data-ttu-id="da274-458">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-458">Int32</span></span>|  
|<span data-ttu-id="da274-459">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="da274-459">LENGTH</span></span>|<span data-ttu-id="da274-460">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-460">Int32</span></span>|  
|<span data-ttu-id="da274-461">ESCALA</span><span class="sxs-lookup"><span data-stu-id="da274-461">SCALE</span></span>|<span data-ttu-id="da274-462">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-462">Int16</span></span>|  
|<span data-ttu-id="da274-463">BASE</span><span class="sxs-lookup"><span data-stu-id="da274-463">RADIX</span></span>|<span data-ttu-id="da274-464">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-464">Int16</span></span>|  
|<span data-ttu-id="da274-465">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="da274-465">NULLABLE</span></span>|<span data-ttu-id="da274-466">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-466">Int16</span></span>|  
|<span data-ttu-id="da274-467">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="da274-467">REMARKS</span></span>|<span data-ttu-id="da274-468">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-468">String</span></span>|  
|<span data-ttu-id="da274-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="da274-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="da274-470">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="da274-471">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="da274-471">Procedures</span></span>  
  
|<span data-ttu-id="da274-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="da274-472">ColumnName</span></span>|<span data-ttu-id="da274-473">DataType</span><span class="sxs-lookup"><span data-stu-id="da274-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="da274-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="da274-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="da274-475">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-475">String</span></span>|  
|<span data-ttu-id="da274-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="da274-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="da274-477">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-477">String</span></span>|  
|<span data-ttu-id="da274-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="da274-479">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-479">String</span></span>|  
|<span data-ttu-id="da274-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="da274-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="da274-481">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-481">Int16</span></span>|  
|<span data-ttu-id="da274-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="da274-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="da274-483">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-483">Int16</span></span>|  
|<span data-ttu-id="da274-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="da274-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="da274-485">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-485">Int16</span></span>|  
|<span data-ttu-id="da274-486">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="da274-486">REMARKS</span></span>|<span data-ttu-id="da274-487">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-487">String</span></span>|  
|<span data-ttu-id="da274-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="da274-489">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="da274-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="da274-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="da274-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="da274-491">ColumnName</span></span>|<span data-ttu-id="da274-492">DataType</span><span class="sxs-lookup"><span data-stu-id="da274-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="da274-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="da274-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="da274-494">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-494">String</span></span>|  
|<span data-ttu-id="da274-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="da274-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="da274-496">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-496">String</span></span>|  
|<span data-ttu-id="da274-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="da274-498">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-498">String</span></span>|  
|<span data-ttu-id="da274-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-499">COLUMN_NAME</span></span>|<span data-ttu-id="da274-500">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-500">String</span></span>|  
|<span data-ttu-id="da274-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-501">COLUMN_TYPE</span></span>|<span data-ttu-id="da274-502">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-502">Int16</span></span>|  
|<span data-ttu-id="da274-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-503">DATA_TYPE</span></span>|<span data-ttu-id="da274-504">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-504">Int16</span></span>|  
|<span data-ttu-id="da274-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-505">TYPE_NAME</span></span>|<span data-ttu-id="da274-506">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-506">String</span></span>|  
|<span data-ttu-id="da274-507">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="da274-507">PRECISION</span></span>|<span data-ttu-id="da274-508">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-508">Int32</span></span>|  
|<span data-ttu-id="da274-509">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="da274-509">LENGTH</span></span>|<span data-ttu-id="da274-510">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-510">Int32</span></span>|  
|<span data-ttu-id="da274-511">ESCALA</span><span class="sxs-lookup"><span data-stu-id="da274-511">SCALE</span></span>|<span data-ttu-id="da274-512">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-512">Int16</span></span>|  
|<span data-ttu-id="da274-513">BASE</span><span class="sxs-lookup"><span data-stu-id="da274-513">RADIX</span></span>|<span data-ttu-id="da274-514">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-514">Int16</span></span>|  
|<span data-ttu-id="da274-515">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="da274-515">NULLABLE</span></span>|<span data-ttu-id="da274-516">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-516">Int16</span></span>|  
|<span data-ttu-id="da274-517">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="da274-517">REMARKS</span></span>|<span data-ttu-id="da274-518">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-518">String</span></span>|  
|<span data-ttu-id="da274-519">SOBRECARGA</span><span class="sxs-lookup"><span data-stu-id="da274-519">OVERLOAD</span></span>|<span data-ttu-id="da274-520">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-520">Int32</span></span>|  
|<span data-ttu-id="da274-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="da274-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="da274-522">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="da274-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="da274-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="da274-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="da274-524">ColumnName</span></span>|<span data-ttu-id="da274-525">DataType</span><span class="sxs-lookup"><span data-stu-id="da274-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="da274-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="da274-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="da274-527">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-527">String</span></span>|  
|<span data-ttu-id="da274-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="da274-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="da274-529">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-529">String</span></span>|  
|<span data-ttu-id="da274-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="da274-531">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-531">String</span></span>|  
|<span data-ttu-id="da274-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-532">COLUMN_NAME</span></span>|<span data-ttu-id="da274-533">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-533">String</span></span>|  
|<span data-ttu-id="da274-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-534">COLUMN_TYPE</span></span>|<span data-ttu-id="da274-535">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-535">Int16</span></span>|  
|<span data-ttu-id="da274-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-536">DATA_TYPE</span></span>|<span data-ttu-id="da274-537">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-537">Int16</span></span>|  
|<span data-ttu-id="da274-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="da274-538">TYPE_NAME</span></span>|<span data-ttu-id="da274-539">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-539">String</span></span>|  
|<span data-ttu-id="da274-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="da274-540">COLUMN_SIZE</span></span>|<span data-ttu-id="da274-541">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-541">Int32</span></span>|  
|<span data-ttu-id="da274-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="da274-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="da274-543">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-543">Int32</span></span>|  
|<span data-ttu-id="da274-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="da274-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="da274-545">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-545">Int16</span></span>|  
|<span data-ttu-id="da274-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="da274-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="da274-547">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-547">Int16</span></span>|  
|<span data-ttu-id="da274-548">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="da274-548">NULLABLE</span></span>|<span data-ttu-id="da274-549">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-549">Int16</span></span>|  
|<span data-ttu-id="da274-550">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="da274-550">REMARKS</span></span>|<span data-ttu-id="da274-551">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-551">String</span></span>|  
|<span data-ttu-id="da274-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="da274-552">COLUMN_DEF</span></span>|<span data-ttu-id="da274-553">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-553">String</span></span>|  
|<span data-ttu-id="da274-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="da274-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="da274-555">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-555">Int16</span></span>|  
|<span data-ttu-id="da274-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="da274-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="da274-557">Int16</span><span class="sxs-lookup"><span data-stu-id="da274-557">Int16</span></span>|  
|<span data-ttu-id="da274-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="da274-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="da274-559">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-559">Int32</span></span>|  
|<span data-ttu-id="da274-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="da274-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="da274-561">Int32</span><span class="sxs-lookup"><span data-stu-id="da274-561">Int32</span></span>|  
|<span data-ttu-id="da274-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="da274-562">IS_NULLABLE</span></span>|<span data-ttu-id="da274-563">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="da274-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="da274-564">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da274-564">See Also</span></span>  
 <span data-ttu-id="da274-565">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="da274-565">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
