# rank-job-apps

A vector function that ranks job applications against a job description, producing a score for each application that reflects its overall fitness for the role.

## Input

The function accepts an object with two required fields:

| Field | Type | Description |
|-------|------|-------------|
| `apps` | `array` of `string` | The job applications to rank. Each string is the full text content of a single application — a resume, cover letter, combined document, or any written candidate submission. Must contain at least one application. |
| `job_description` | `string` | The job description to rank applications against. This includes the role title, responsibilities, required and preferred qualifications, and any other context the employer has provided about the position. |

### Example Input

```json
{
  "apps": [
    "Jane Doe\nSenior Software Engineer with 8 years of experience in distributed systems...",
    "John Smith\nRecent CS graduate with internship experience at two startups...",
    "Alex Chen\nFull-stack developer with 5 years building e-commerce platforms..."
  ],
  "job_description": "We are looking for a Senior Backend Engineer to design and maintain scalable microservices..."
}
```

## Output

The function returns an array of numerical scores, one per application, in the same order as the input `apps` array. Higher scores indicate stronger overall fit for the role. The scores can be used to sort applications from most to least promising.

## What It Evaluates

The function synthesizes six distinct dimensions of evaluation. No single dimension dominates — the final ranking reflects a holistic assessment across all six.

### 1. Relevance of Experience

How directly does the candidate's professional history map onto the responsibilities and domain of the open role? This is not about counting years of experience but about evaluating the nature and context of that experience. A candidate with three years in a closely related role may outrank someone with ten years in a tangentially related field.

### 2. Skills Alignment

Does the candidate demonstrate the specific technical and interpersonal skills called for in the job description? The function favors applications that weave skills into a narrative of applied capability — showing how skills were used in practice — over those that merely list competencies without context.

### 3. Demonstrated Impact

Does the candidate show evidence of measurable results and tangible accomplishments? The function looks for quantified achievements, before-and-after descriptions, and concrete examples of value driven — such as growing revenue, reducing costs, improving processes, or shipping products. Applications that describe outcomes rank higher than those that only list responsibilities.

### 4. Clarity and Communication

How well-written is the application itself? This dimension evaluates structure, conciseness, professionalism, grammatical correctness, and overall readability — independent of the application's content. A clearly organized and precisely articulated application reflects communication skills and attention to detail that matter in nearly every professional context.

### 5. Career Trajectory and Growth

Does the candidate's career show a pattern of increasing responsibility, skill development, and intentional progression? The function considers whether the role being applied for represents a logical next step in the candidate's professional journey. Upward momentum and a demonstrated capacity for learning rank higher than stagnant or unexplained career paths.

### 6. Tailoring and Intentionality

Was the application crafted specifically for this role? The function looks for explicit references to the company, the position, or the challenges mentioned in the job description. Applications that draw direct connections between the candidate's background and the employer's needs rank higher than generic submissions that could be sent to any employer without modification.

## Use Cases

- **Recruiter triage**: Quickly identify which candidates in a batch deserve closer attention, rather than reading every application with equal depth.
- **High-volume hiring**: Create a defensible, consistent shortlist when seasonal positions or popular roles attract hundreds of applicants.
- **Internal mobility**: Evaluate internal transfer and promotion applications on merit and fit rather than proximity or politics.
- **Calibration and bias detection**: Compare your team's intuitive rankings against the function's output to surface overlooked candidates and reflect on potential blind spots in your evaluation process.

## Important Notes

- The function **ranks** applications — it does not make hiring decisions. The output is a starting point for human decision-making, not a replacement for it.
- The job description is the lens through which all applications are evaluated. A more detailed and specific job description will produce more meaningful rankings.
- Applications can be any text-based candidate submission: resumes, cover letters, combined documents, or free-form written responses.
- The function evaluates what candidates present in their applications. It cannot assess qualities not reflected in the submitted text.