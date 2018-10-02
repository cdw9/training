.. _reducer_tests-label:

=============================
Write Tests For Your Reducers
=============================

Reducer Tests
=============

Since reducers are just pure functions with input and output they are really
easy to write unit tests for. We'll start by adding a test for the
:file:`ADD_TODO` action in a file called :file:`reducers/faq.test.js`:

::

    import faq from "./faq";

    describe("faq", () => {
      it("is able to handle the add faq item action", () => {
        expect(
          faq([], {
            type: "ADD_FAQ_ITEM",
            question: "What is the answer to life the universe and everything?",
            answer: 42
          })
        ).toEqual([
          {
            question: "What is the answer to life the universe and everything?",
            answer: 42
          }
        ]);
      });
    });

Exercise
========

Add the unit tests for the edit and the delete actions for the reducer.

..  admonition:: Solution
    :class: toggle

    ::

        it("is able to handle the edit faq item action", () => {
          expect(
            faq(
              [
                {
                  question: "What is the answer to life the universe and everything?",
                  answer: 42
                }
              ],
              {
                type: "EDIT_FAQ_ITEM",
                index: 0,
                question: "What is the answer to life the universe and everything?",
                answer: 43
              }
            )
          ).toEqual([
            {
              question: "What is the answer to life the universe and everything?",
              answer: 43
            }
          ]);
        });

        it("is able to handle the delete faq item action", () => {
          expect(
            faq(
              [
                {
                  question: "What is the answer to life the universe and everything?",
                  answer: 42
                }
              ],
              {
                type: "DELETE_FAQ_ITEM",
                index: 0
              }
            )
          ).toEqual([]);
        });
