**Revision: New Screenshot of Loyalty Discount Calculation including Tier Percentage Added.**


**All 6 screenshots of my test cases along with their provided responses are given in this folder.**

*The 6 test cases are:*

Test 1 — Order Tracking

agentcore invoke '{"prompt": "Can you track order ORD-001?", "customer_id": "CUST-123", "session_id": "t1"}'
Expected: shipping status, tracking number TRK987654321, carrier UPS, estimated delivery date.

Test 2 — Refund Processing

agentcore invoke '{"prompt": "I want to return my Kindle Paperwhite (ORD-002). Please initiate a refund.", "customer_id": "CUST-123", "session_id": "t2"}'
Expected: refund ID, APPROVED status, "3-5 business days" message.

Test 3 — Knowledge Base (RAG)

agentcore invoke '{"prompt": "What are the benefits of the Platinum loyalty tier?", "customer_id": "CUST-123", "session_id": "t3"}'
Expected: free same-day shipping, 15% discount, priority support (retrieved from Knowledge Base).

Test 4 — Long-Term Memory (two sessions)

 Session A — introduce yourself
agentcore invoke '{"prompt": "Hi, I am Jane. I prefer concise responses.", "customer_id": "CUST-123", "session_id": "s-A"}'

Wait at least 30 seconds for memory extraction

 Session B — verify recall (new session, same customer)
agentcore invoke '{"prompt": "Do you remember my name and communication preference?", "customer_id": "CUST-123", "session_id": "s-B"}'
Expected: agent recalls "Jane" and the preference for concise responses.

Test 5 — Loyalty Discount Calculation

agentcore invoke '{"prompt": "I am a Gold member with 4250 points. Calculate my discount on a $150 standard order.", "customer_id": "CUST-123", "session_id": "t5"}'
Expected: points redeemed, tier discount 10%, correct final total, remaining points.

Test 6 — Browser Tool

agentcore invoke '{"prompt": "Go to https://www.udacity.com and tell me the page title.", 
