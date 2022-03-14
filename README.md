# 2022graphics
```c++
#include <GL/glut.h>
void display()
{
    glClear( GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT );
    glColor3f(1,1,0);
    glutSolidTeapot(0.3);
    glutSwapBuffers();
}
int main(int argc,char**argv)
{
    glutInit(&argc,argv);
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_DEPTH);
    glutCreateWindow("week03的視窗");
    glutDisplayFunc(display);
    glutMainLoop();
    return 0;
}

```
```c++
#include <GL/glut.h>
void display()
{
    glClear( GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT );
    glColor3f(1,1,0);
     glBegin(GL_TRIANGLES);

                glColor3f(1.0f, 0.0f, 0.0f);   glVertex2f(0.0f,   1.0f);
                glColor3f(0.0f, 1.0f, 0.0f);   glVertex2f(0.87f,  -0.5f);
                glColor3f(0.0f, 0.0f, 1.0f);   glVertex2f(-0.87f, -0.5f);

            glEnd();
    glutSwapBuffers();
}
int main(int argc,char**argv)
{
    glutInit(&argc,argv);
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_DEPTH);
    glutCreateWindow("week03的彩色三角形視窗");
    glutDisplayFunc(display);
    glutMainLoop();
    return 0;
}

```
```c++
#include <GL/glut.h>
#include <stdio.h>
int mouseX=0,mouseY=0,N=0;
int mx[100],my[100];
void display()
{
    glClear( GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT );
    glColor3f(1,1,0);
    glBegin(GL_LINE_LOOP);
        for(int i=0;i<N;i++){
            glVertex2f((mx[i]-150)/150.0,-(my[i]-150)/150.0);
        }
    glEnd();
    glutSwapBuffers();
}
void mouse(int button,int state,int x,int y)
{
    mouseX=x; mouseY=y;
    if(state==GLUT_DOWN){
        printf("    glVertex2f( (%d-150)/150.0,-(%d-150)/150.0);\n",x,y);
        N++;
        mx[N-1]=x; my[N-1]=y;
    }
}
int main(int argc,char**argv)
{
    glutInit(&argc,argv);
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_DEPTH);
    glutCreateWindow("week04 mouse");

    glutDisplayFunc(display);
    glutMouseFunc(mouse);
    glutMainLoop();
    return 0;
}
```
```c++
#include <GL/glut.h>
void myTeapot(float x,float y)
{
    glPushMatrix();
        glTranslatef(x,y,0);
        glutSolidTeapot(0.3);
    glPopMatrix();
}
void display()
{
    glClear( GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT );
    glColor3f(1,0,0);
    myTeapot(+0.5,+0.5);
    myTeapot(+0.5,-0.5);
    myTeapot(-0.5,+0.5);
    myTeapot(-0.5,-0.5);

    glutSwapBuffers();
}
int main(int argc,char**argv)
{
    glutInit(&argc,argv);
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_DEPTH);
    glutCreateWindow("week04 translate");
    glutDisplayFunc(display);
    glutMainLoop();
    return 0;
}
```
