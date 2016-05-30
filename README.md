# matrix

#include <stdio.h>

#include <stdbool.h>

bool match(char *first, char *second)

{

	if (*first == '\0' && *second == '\0')

		return true;

	if (*first == '*' && *(first+1) == '\0' && *second != '\0')

		return true;

	if (*first == '?' && *(first+1) == '\0' && *second == '\0')

		return true;

	if (*first == '*' && *(first+1) != '\0' && *second == '\0')

		return false;

	if (*first == '?' && *(first+1) == *second)

		return match(first+2, second+1);

	if (*first == '?' || *first == *second)

		return match(first+1, second+1);

	if (*first == '*')

		return match(first+1, second) || match(first, second+1);

	return false;

}

void test(char *first, char *second)

{
 match(first, second)? puts("Yes"): puts("No");
 }

int main()

{

        char *a=(char*)"s*i";

	char *c=(char*)"s?wa?i";

     	char *b=(char*)"swati";

	char *d=(char*)"swatibhat";

	char *e=(char*)"swa*ya";

	char *f=(char*)"swati?hat";

	char *g=(char*)"s*wa?ibha*t";

	char *h=(char*)"swati*";

	char *i=(char*)"swatibhat?";

	char *j=(char*)"swati?bha?t";



     	test(a, b);

	test(c, b);

	test(e, d);

	test(f, d);

	test(g, d);

	test(h, d);

	test(i, d);

	test(j, d);

  return 0;
}


